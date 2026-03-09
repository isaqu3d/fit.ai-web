# fit.ai — Web

Frontend for an AI-powered personal fitness trainer 🏋️

![Next.js](https://img.shields.io/badge/Next.js-16.x-000000?style=for-the-badge&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-19.x-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4.x-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Zod](https://img.shields.io/badge/Zod-4.x-3E67B1?style=for-the-badge&logo=zod&logoColor=white)
![pnpm](https://img.shields.io/badge/pnpm-10.x-F69220?style=for-the-badge&logo=pnpm&logoColor=white)

---

## 🚀 About

**fit.ai Web** is the frontend for an intelligent fitness application. It allows users to create personalized workout plans, track workout sessions, and interact with an AI personal trainer that generates and adjusts training programs based on individual goals and physical data.

---

## 🛠 Technologies

| Technology | Purpose |
|---|---|
| **Next.js 16 (App Router)** | React framework with SSR and file-based routing |
| **React 19** | UI library |
| **TypeScript 5** | Type-safe development |
| **Tailwind CSS 4** | Utility-first styling |
| **shadcn/ui** | Accessible, composable UI components |
| **better-auth** | Authentication (email/password, Google, sessions) |
| **React Hook Form + Zod** | Form management and schema validation |
| **TanStack Query** | Server state management and data fetching |
| **Orval** | Auto-generation of API functions and hooks from OpenAPI spec |
| **AI SDK** | AI personal trainer chat integration |
| **dayjs** | Date manipulation and formatting |

---

## 📁 Project Structure

```
fit.ai-web/
├── app/
│   ├── auth/                      # Authentication page (login/register)
│   ├── onboarding/                # New user onboarding flow
│   ├── profile/                   # User profile page
│   ├── stats/                     # Training statistics page
│   ├── workout-plans/
│   │   └── [id]/                  # Workout plan detail and day tracking
│   ├── _components/               # Shared layout components
│   │   ├── bottom-nav.tsx
│   │   ├── chat.tsx
│   │   ├── consistency-tracker.tsx
│   │   └── workout-day-card.tsx
│   ├── _lib/
│   │   ├── auth-client.ts         # better-auth client setup
│   │   ├── fetch.ts               # Fetch utilities
│   │   └── api/
│   │       └── fetch-generated/   # Orval-generated server-side fetch functions
│   ├── layout.tsx                 # Root layout
│   ├── page.tsx                   # Home page
│   └── globals.css                # Global styles and theme variables
├── components/
│   └── ui/                        # shadcn/ui components
├── lib/
│   └── utils.ts                   # Utility functions (cn, etc.)
├── public/                        # Static assets
├── orval.config.ts                # Orval code generation config
├── components.json                # shadcn/ui config
└── .env.example
```

### Request Flow

```
Page (Server Component) → fetch-generated → API → initialData → TanStack Query Hook (Client Component)
```

---

## ⚙️ How to Run

### Prerequisites

- Node.js 24+
- pnpm 10+
- [fit.ai API](https://github.com/isaqu3d/fit.ai-api) running locally

### 1. Clone the repository

```sh
git clone git@github.com:isaqu3d/fit.ai-web.git
cd fit.ai-web
```

### 2. Install dependencies

```sh
pnpm install
```

### 3. Set up environment variables

```sh
cp .env.example .env
```

Edit `.env` and fill in the required values:

```env
NEXT_PUBLIC_API_URL=      # URL of the fit.ai API (e.g. http://localhost:4949)
NEXT_PUBLIC_BASE_URL=     # Base URL of this app (e.g. http://localhost:3000)
```

### 4. Start the development server

```sh
pnpm dev
```

The app will be available at `http://localhost:3000`.

---

## 🔐 Authentication

Authentication is handled by **better-auth** using email/password and Google OAuth strategies. Session verification is done directly in each page component via `authClient.useSession()`. Protected pages redirect to `/auth` when the user is not authenticated.

---

## 🎨 Theming

The project uses **Tailwind CSS v4** with a custom theme defined via CSS variables in `globals.css`. Colors use the `oklch()` color space and support both light and dark modes. All components rely exclusively on theme variables — no hardcoded colors.

---

## 📝 License

[MIT License](LICENSE)

Made by [Isaque de Sousa](https://github.com/isaqu3d) — give a ⭐️!
