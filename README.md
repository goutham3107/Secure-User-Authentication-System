# Secure User Authentication System

A premium, modern full-stack web application demonstrating a complete and secure user authentication flow. Built from the ground up using **Next.js 16**, **Prisma**, **Tailwind CSS**, and **JSON Web Tokens (JWT)**.

## 🚀 Features

- **Secure User Registration & Login**: Full authentication flow with form validations.
- **Password Hashing**: Uses `bcryptjs` to encrypt user passwords before saving them to the database, ensuring maximum security.
- **Stateless Session Management**: Generates encrypted JSON Web Tokens (using `jose`) securely stored in **HTTP-only cookies** to mitigate XSS (Cross-Site Scripting) attacks.
- **Route Protection**: Next.js `proxy.ts` (formerly middleware) guards protected routes like `/dashboard`, immediately redirecting unauthenticated users to the login screen.
- **Premium UI/UX**: Designed using Tailwind CSS featuring glassmorphism, responsive layouts, subtle micro-animations, and rich aesthetic gradients.
- **Role-Based Structure**: Database and session token include user roles for simple extendability to role-based access control (RBAC).

## 🛠️ Tech Stack

- **Framework**: [Next.js 16](https://nextjs.org/) (App Router)
- **Database**: [SQLite](https://www.sqlite.org/) (Local File Database)
- **ORM**: [Prisma](https://www.prisma.io/)
- **Authentication**: Custom JWT implementation with [`jose`](https://github.com/panva/jose) and HttpOnly Cookies
- **Security**: [`bcryptjs`](https://www.npmjs.com/package/bcryptjs) for password hashing
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/)

## 📂 Project Structure

- `src/app/api/auth/` - Contains the serverless API routes for login, register, and logout.
- `src/lib/auth.ts` - Core authentication logic containing encryption/decryption of the JWT session payload.
- `src/proxy.ts` - Edge middleware that acts as a secure proxy to block unauthorized access to protected routes.
- `src/lib/db.ts` - Singleton Prisma client instance.
- `prisma/schema.prisma` - Defines the database models (User).

## 💻 Getting Started

### Prerequisites
Make sure you have Node.js (v18+) and npm installed on your machine.

### Installation

1. **Clone the repository:**
   ```bash
   git clone <your-repo-url>
   cd auth-system
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Initialize the Database:**
   Generate the Prisma Client and push the database schema to your local SQLite database:
   ```bash
   npx prisma db push
   ```

4. **Start the development server:**
   ```bash
   npm run dev
   ```

5. **Open the application:**
   Navigate to [http://localhost:3000](http://localhost:3000) in your browser.

## 🛡️ Security Considerations
- **Environment Variables**: In a production environment, always ensure your `JWT_SECRET` in `src/lib/auth.ts` is sourced from a secure `.env` file instead of being hardcoded.
- **Secure Cookies**: The `Secure` flag on the session cookie is dynamically enabled in production environments automatically.

## 📝 License
This project is open-source and available under the MIT License.
