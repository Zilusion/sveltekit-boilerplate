# Production-Ready SvelteKit Boilerplate

This is an opinionated boilerplate for building robust, professional-grade SvelteKit applications. It comes pre-configured with a comprehensive toolchain for quality assurance, development consistency, and a scalable architecture from day one.

The goal of this template is to provide a solid foundation, allowing you to focus on building features instead of spending days on project setup.

---

## What's Included?

- **Framework**: [SvelteKit](https://kit.svelte.dev/) powered by [Vite](https://vitejs.dev/)
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/blog/tailwindcss-v4-alpha) with a CSS-first configuration (`@theme`).
- **Containerization**: [Docker](https://www.docker.com/) setup with multi-stage builds for both development (with hot-reloading via `watch`) and production (with Nginx).
- **Component-Driven Development**: [Storybook](https://storybook.js.org/) for building and documenting components in isolation.
- **Testing**: [Vitest](https://vitest.dev/) for unit and component testing.
- **Code Quality & Formatting**:
  - [ESLint](https://eslint.org/) for identifying and fixing code issues.
  - [Prettier](https://prettier.io/) for consistent code formatting.
  - [Stylelint](https://stylelint.io/) for CSS quality control.
- **Git Hooks & Commit Standards**:
  - [Husky](https://typicode.github.io/husky/) for managing git hooks.
  - [lint-staged](https://github.com/okonet/lint-staged) to run linters on staged files.
  - [commitlint](https://commitlint.js.org/) to enforce conventional commit messages.
- **Absolute Imports**: Pre-configured with `$lib` for clean and simple import paths.

## Architectural Philosophy

This boilerplate is not just a collection of tools; it's a philosophy for building maintainable applications:

1.  **Component-Driven Development**: We build UIs from the bottom up, starting with small, reusable components. Storybook is our primary workshop for this.
2.  **Utility-First Styling**: We use Tailwind CSS to avoid writing custom CSS as much as possible. Design tokens (colors, spacing, etc.) are centralized in `src/app.css` under the `@theme` directive, acting as the single source of truth.
3.  **Automated Quality Gates**: The combination of Husky, lint-staged, and linters ensures that no poorly formatted or error-prone code ever reaches the main branch.
4.  **Consistent Environments**: Docker guarantees that the application runs the same way on every developer's machine and in production. No more "it works on my machine" issues.

## Getting Started

### Using as a Template

The best way to use this project is to create a new repository from this template on GitHub.

1.  Click the "Use this template" button on the repository page.
2.  Choose a name for your new repository.
3.  Clone your new repository to your local machine.

### Local Development

This project is designed to be run inside Docker. Ensure you have Docker and Docker Compose installed.

1.  **Install Dependencies:**
    _The first time, Docker will do this for you. If you add a new dependency, run:_

    ```bash
    pnpm install
    ```

2.  **Run the Development Server:**
    _This command starts the SvelteKit application with hot-reloading enabled._

    ```bash
    docker-compose up --profile develop --build --watch
    ```

    The application will be available at `http://localhost:5173`.

3.  **Run Storybook:**
    _To work on components in isolation, you'll need to run Storybook. You can do this by creating a `docker-compose.override.yml` file or by running it directly inside the running container._

## Available Scripts

This project includes a set of useful scripts defined in `package.json`:

- `pnpm dev`: Starts the SvelteKit development server.
- `pnpm build`: Builds the application for production and packages the library.
- `pnpm preview`: Previews the production build locally.

### Code Quality

- `pnpm check`: Runs all checks (types, format, linting, styles). Ideal for CI/CD pipelines.
- `pnpm check:types`: Validates TypeScript types.
- `pnpm check:format`: Checks for formatting issues with Prettier.
- `pnpm check:lint`: Checks for code issues with ESLint.
- `pnpm check:styles`: Checks for CSS issues with Stylelint.

- `pnpm fix`: Automatically fixes all fixable issues.
- `pnpm fix:format`: Fixes formatting with Prettier.
- `pnpm fix:lint`: Fixes code issues with ESLint.
- `pnpm fix:styles`: Fixes CSS issues with Stylelint.

### Testing & Storybook

- `pnpm test`: Runs all unit tests.
- `pnpm storybook`: Starts the Storybook development server.
- `pnpm build-storybook`: Builds Storybook as a static web application.

### Custom Scripts

- `pnpm icons:generate`: A custom script to process SVG files from `/scripts/icons` and generate the typed `icons.ts` file.

## Project Structure

- `.husky/`: Configuration for git hooks.
- `.storybook/`: Configuration for Storybook.
- `scripts/`: Holds custom Node.js scripts for automating tasks (e.g., icon generation).
- `src/lib/`: This is the heart of your application/library.
  - `components/`: Reusable Svelte components.
  - `utils/`: Utility functions.
- `src/routes/`: Contains the pages for your SvelteKit application (your documentation site).
- `static/`: Static assets that are copied to the build directory as-is.
- `Dockerfile` & `Dockerfile.dev`: Docker configurations for production and development.
- `docker-compose.yml`: Defines the services for running the application with Docker.
