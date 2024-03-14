# Environment Setup

- Next.js 14.0.3
npx create-next-app@14.0.3 antonio-twitch-clone
```
√ Would you like to use TypeScript? Yes
√ Would you like to use ESLint? Yes
√ Would you like to use Tailwind CSS? Yes
√ Would you like to use `src/` directory? No
√ Would you like to use App Router? (recommended) Yes
√ Would you like to customize the default import alias (@/\*)? No
```
`cd folder`

npx shadcn-ui@latest init
```
√ Would you like to use TypeScript (recommended)? ... yes
√ Which style would you like to use? » Default
√ Which color would you like to use as base color? » Neutral
√ Where is your global CSS file? ... app/globals.css
√ Would you like to use CSS variables for colors? ... yes
```

```
npx shadcn-ui@latest add button
npm run dev
```

# Folders Setup

...

# Authentication

Clerk setup: https://clerk.com/ - login - add application

```
application name: antonio-trello 
turn off email address
create application
copy API KEYS to .env
.gitignore .env
npm i @clerk/nextjs
```

.env
```
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY= 
CLERK_SECRET_KEY= 
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in 
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up 
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/ 
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/
```

# Dark Mode

`npm i next-themes@0.2.1 @clerk/themes@1.7.9`

# Database

NeonDB: https://neon.tech/ - login - create service

```
npm i -D prisma
npm i @prisma/client
npx prisma init
npx prisma generate
npx prisma db push
npx prisma studio
```

.env 
```
DATABASE_URL=
```

.package.json
```
"scripts": {
    "postinstall": "prisma generate"
  },
```

# Local Tunnel

Ngrok
```
Download & Open Ngrok - https://ngrok.com/download
create account - add-authtoken
ngrok http 3000 - use https link
npm run dev
.
stable url - https://dashboard.ngrok.com/ - Cloud Edge - Domains - new domain
ngrok http -domain=... 3000 - instead of ngrok http 3000
```

# Clerk Webhook

```
enable Username in Clerk Dashboard
Goto tab User & Authentication - Email, Phone, Username.
Enable Username
Then click Gear next to Username.
Disable "Sign-in" but keep require.
.
delete all users from clerk
info at https://clerk.com/docs/integrations/webhooks/sync-data
https://dashboard.clerk.com/ - webhooks - add endpoint - paste ngrok http + "/api/webhooks/clerk"
Message Filtering - enable user - create - copy signin secret to .env
npm i svix
restart ngrok & validate ngrok http + /api/webhooks/clerk - show "null"
clerk webhook - Testing - send user.created - send example - validate show -  ⨯ PrismaClientValidationError: Invalid `prisma.user.create()` invocation:
validate npx prisma studio - open http://localhost:3000 - when create user studio show "User" data
```

.env
```
CLERK_WEBHOOK_SECRET=
```

# Navbar

```
npm i query-string@8.1.0
npx shadcn-ui@latest add input
```

# Sidebar

```
npx shadcn-ui@latest add tooltip
npm i usehooks-ts@2.9.1 zustand@4.4.7
```

# Recommended List

`npx shadcn-ui@latest add avatar skeleton`

# Hydration Error

Read @ https://www.joshwcomeau.com/react/the-perils-of-rehydration/

# Follow Service

```
npm i sonner
npx prisma generate
npx prisma db push
```

# Follow List

...

# Block Service

Notice: block onClick is broken. Only used for testing.

```
npx prisma generate
npx prisma db push
```

# Creator Dashboard

...

# Stream Model

```
remove all users - in clerk & db
npx prisma migrate reset
npx prisma db push
npx prisma generate
```

# Chat Settings

`npx shadcn-ui@latest add switch`

# Key Settings

`npx shadcn-ui@latest add alert dialog select`

# Ingress

```
visit https://livekit.io - signin - create new project - antonio-twitch - finish
settings tab - keys - add new key "development"
copy the 3 keys to .env
.
get LIVEKIT_API_URL by analytics tab - copy top link - + "https://" at beginning
npm i @livekit/components-react@1.4.2 livekit-client@1.15.4 livekit-server-sdk@1.2.7
.
generate connection - RTMP
```

.env
```
LIVEKIT_API_URL=
LIVEKIT_API_KEY=
LIVEKIT_API_SECRET=
NEXT_PUBLIC_LIVEKIT_WS_URL=
```

# OBS Crash Course

```
https://obsproject.com/ - download & open
Scenes - (+) - "obs demo"
Sources - (+) - "screen capture" - select display
Sources - (+) - "audio input capture" - 
Controls - settings 
- video - same base & output resolution
- output - output mode "advanced" 
- streaming tab
- streaming settings - video encoder "x264"
- encoder settings - rate control CBR / bitrate 3500 kpbs / cpu veryfast
- recording tab - recording path / format mkv / 
.
copy server url from site -
- stream - Custom - add server / add stream key - click ok
.
Controls - start streaming
.
validate stream in https://cloud.livekit.io/ - Egress/Ingress - status publishing
```

# Livekit Webhook

```
add webhook at Livekit Page - Project - Settings - Webhook tab
- name: "development" - url: paste ngrok link + "/api/webhooks/livekit" - add signin api key correctly
.
localhost - login - dashboard - keys - generate RTMP - copy keys
obs - settings - stream tab - paste server & stream key - start stream
localhost - signout - validate live text is shown in sidebar recommended list. 
```

# Deployment

foreach
```
git add .
git commit -m "XX: message"
git push
validate deployment succeed
```

once
```
github.com/new - name "antonio-twitch" - create repo
use second option - "push an existing repo"
.
vercel.com/new - import "antonio-twitch" - deploy
settings - environment variables - add from .env
```