# 10x-cards

## Project Description

10x-cards is a web application designed to facilitate learning through the use of educational flashcards. The project streamlines the creation, validation, and management of flashcards, offering both manual creation and AI-assisted generation. Users can register, log in, create flashcards with character limits (200 characters for the front, 400 for the back), edit them, delete them, and review usage statistics.

## Tech Stack

- **Frontend:** Astro 5, React 19, TypeScript 5, Tailwind CSS 4, Shadcn/ui
- **Backend:** Supabase for PostgreSQL database, authentication, and a comprehensive back-end solution
- **AI Integration:** Openrouter.ai for accessing various AI models (OpenAI, Anthropic, Google, etc.) to generate flashcard content
- **CI/CD & Hosting:** Github Actions for continuous integration and delivery, DigitalOcean with Docker for hosting
- **Node Version:** 22.14.0 (as specified by the .nvmrc file)

## Getting Started Locally

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/10x-cards.git
   cd 10x-cards
   ```
2. **Install dependencies:**
   ```bash
   npm install
   ```
3. **Run the development server:**
   ```bash
   npm run dev
   ```
4. **Build for production:**
   ```bash
   npm run build
   ```

Ensure that you are using Node.js version 22.14.0 as specified in the `.nvmrc` file.

## Available Scripts

- `npm run dev` - Starts the Astro development server.
- `npm run build` - Builds the project for production.
- `npm run preview` - Previews the production build locally.
- `npm run astro` - Runs Astro CLI commands.
- `npm run lint` - Runs ESLint to check for code quality.
- `npm run lint:fix` - Fixes linting errors automatically using ESLint.
- `npm run format` - Formats the code using Prettier.

## Project Scope

10x-cards is an educational flashcards system that aims to simplify the learning process:

- **User Management:** Registration and login system with automatic post-registration login.
- **Flashcard Creation:** 
  - Manual creation via a form with character limits (200 for front, 400 for back).
  - Automatic generation of flashcards using AI, with the option for the user to validate, edit, or delete generated flashcards.
- **Validation:** Real-time validation of flashcard content ensuring character limits are adhered to.
- **Flashcard Management:** Allows editing and deletion of flashcards with confirmation prompts.
- **Statistics:** Tracks and displays statistics on flashcard generation and user interactions to support decision-making.

Project boundaries include:

- Support for web applications only (no mobile application).
- External sharing or import of flashcards is not covered.
- The system does not implement advanced repetition algorithms.

## Project Status

This project is in early development. Features are being actively developed and refined based on user feedback and performance testing.

## License

This project is licensed under the MIT License. 