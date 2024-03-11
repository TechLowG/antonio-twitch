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