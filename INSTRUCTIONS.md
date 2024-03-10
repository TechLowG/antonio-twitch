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