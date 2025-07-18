# Momentum Project

This project is an application called **Momentum**, developed with Angular. Its main goal is to allow users to capture, cherish, and relive their most precious memories through a personal digital capsule. The application features an adaptive layout structure that dynamically changes based on the user's authentication status, offering different views and functionalities.

## Main Features

- **Framework:** Angular 19
- **Styling:** SCSS, using Angular Material for UI components.
- **Authentication:**
  - Simple login system (demo credentials: `lemoncoder` / `1234`).
  - Authentication state is managed using `localStorage`.
  - `AuthService` for authentication logic.
  - `AuthGuard` to protect routes and manage redirects.
- **Dynamic Layout:**
  - Public header for unauthenticated users.
  - Private header for authenticated users.
  - Persistent footer.
- **Memory Management:**
  - CRUD operations for memories using `MemoryService`.
  - Mock data provided for demonstration purposes.
  - Memory interface with id, title, date, description, emoji, and imageUrl properties.
- **Routing:** Manages navigation between different public and private pages.
- **Responsive Design**: The application is designed to be responsive, providing an optimal user experience across various devices and screen sizes (desktop, tablet, mobile).

## Project Structure

The main source code is located within the `src/app/` folder:

- `core/`: Contains the core logic of the application:
  - `auth.service.ts` and `auth.guard.ts`: Authentication management.
  - `memory/`: Memory-related services and models:
    - `memory.service.ts`: Service for CRUD operations on memories.
    - `memory.model.ts`: Memory interface definition.
    - `memory.mock.ts`: Mock data for memories.
  - `utils/`: Utility functions:
    - `date-format.util.ts`: Date formatting utilities.
    - `emoji.util.ts`: Emoji-related utilities and constants.
    - `id-generator.util.ts`: ID generation utilities.
- `layout/`: Reusable visual components that make up the page structure:
  - `header-public/`: Header for the public section.
  - `header-private/`: Header for the private section (authenticated users).
  - `public-menu/`: Contains menu items for the public header.
  - `private-menu/`: Contains menu items for the private header.
  - `footer/`: Common footer.
- `pages/`: Components representing the different views/pages of the application:
  - `home/`: Homepage and welcome page.
  - `login/`: Login page.
  - `about/`: Informational page "About Momentum".
  - `dashboard/`: Main panel for authenticated users, displaying the last three memories.
  - `create/`: Editor to create new memories.
  - `gallery/`: Visual gallery of saved memories.
  - `profile/`: User profile page (under development).
- `shared/`: Shared components that can be used in various parts of the application.
  - `memory-card/`: Defines the visual structure of each memory card displayed in the application (e.g., in the Gallery or Dashboard).
- `app.component.ts` and `app.component.html`: Root component of the application, manages the main layout and the inclusion of headers based on authentication status.
- `app.routes.ts`: Defines the application's navigation routes.
- `styles.scss`: Global application styles.
- `_mixins.scss`: SASS mixins for style utilities.

## Detailed Functionalities

### Application Concept: Momentum

Momentum is designed to be a personal digital capsule where users can save and relive their most significant moments. It focuses on the importance of treasuring memories.

### Authentication

The authentication system is basic and designed for demonstration purposes.

- **Login**: Accessed via the `/login` route. Hardcoded credentials are:
  - User: `lemoncoder`
  - Password: `1234`
- **Route Protection**:
  - Routes like `/dashboard`, `/create`, `/gallery`, and `/profile` require the user to be authenticated. If an unauthenticated user tries to access them, they are redirected to `/home`.
  - If an already authenticated user tries to access `/login` or `/home`, they are redirected to `/dashboard`.
- **Persistence**: Authentication state and username are stored in `localStorage`.

### Navigation and Layout

The application adapts its interface and navigation options based on whether the user is logged in or not.

#### Public Menu (Visible to unauthenticated users)

- **Home**:
  - Welcome message: "Keep your moments alive."
  - Description: "Capture your memories and relive them anytime you want."
- **Login**:
  - Call to action: "Access your digital capsule."
- **About**:
  - Content: Explanation of the Momentum app.

#### Private Menu (Visible to authenticated users)

- **Dashboard**:
  - Purpose: Displays the three most recent memories.
  - Future implementation: Phrases like "Today 2 years ago…" or a visual grid of memories.
- **Gallery**:
  - Purpose: Presents a visual grid of the user's memories.
  - Details: Includes photos, titles, and dates for each memory.
- **Create**:
  - Purpose: Editor to add memories.
  - Available fields:
    - Title (max 100 characters)
    - Date (using Angular Material datepicker)
    - Description (max 700 characters)
    - Emotion (dropdown to select up to 3 representative emojis)
    - Image (file upload with preview functionality)
- **Profile** (not yet implemented):
  - Welcome message: "Welcome back, [username]" (e.g., "Welcome back, lemoncoder")
  - Information displayed:
    - "First memory on: [date_first_memory]" (e.g., "2023-05-19")
    - "Total memories: [total_number_memories]" (e.g., "28")
    - "Most used emoji: [emoji]" (e.g., "😊")

### Footer

- **Footer**: Contains copyright information and is visible on all pages.

## Available Scripts

In the project root, you can find the following scripts in `package.json`:

- `npm start` or `ng serve`: Starts the development server. Access the app at `http://localhost:4200/`.
- `npm run build` or `ng build`: Compiles the application for production.
- `npm test` or `ng test`: Runs unit tests using Karma and Jasmine.
- `npm run watch` or `ng build --watch --configuration development`: Compiles in development mode and watches for changes.

## Future Implementations

- **Memory Time Machine**: A feature to "travel in time" and revisit memories from specific dates or periods.
- **Memory Prompts**: Suggestions or questions to inspire the user to remember and record new moments.
- **Memory Editing**: Allow users to modify existing memories (currently, the `Create` editor only allows adding new ones).
- **Comprehensive Testing Implementation**: Develop and run unit, integration, and end-to-end tests to ensure application quality and stability.
- **Memory Search and Filtering**: Implement functionality to search for memories based on keywords, dates, emotions, or other criteria, and filter them accordingly.
- **Folder Organization**: Allow users to organize their memories into custom folders for better management.
- **Profile Page Implementation**: Complete the profile page with user statistics and memory insights.

## Authors

- Guste Gaubaite - Angular Laboratory Project for Lemoncode Frontend Master.
