# Neiphos 2k26 Timetable

A modern, responsive web application for displaying the Neiphos 2k26 festival timetable. Built with SvelteKit and designed for easy content management and offline support.

![Screenshot](screenshot.jpg)

## Features

- **Real-time Schedule Display**: Shows currently playing acts and upcoming performances
- **Multi-stage Support**: Displays timetables for multiple stages with custom icons
- **Search Functionality**: Find acts quickly with fuzzy search across all stages
- **Favorites**: Mark and track favorite acts with persistent storage
- **CMS**: Content management system for easy schedule updates
- **PWA**: Installable progressive web app with offline support

## Tech Stack

- **Framework**: SvelteKit 2.x with Svelte 5
- **Styling**: Tailwind CSS 4.x
- **PWA**: Vite PWA plugin for offline functionality
- **CMS**: Sveltia static site CMS for content management
- **Build**: Vite with SvelteKit static adapter

## Development

### Prerequisites

- Node.js (v22 or higher)
- Yarn package manager

### Getting Started

1. Clone the repository:

```bash
git clone https://github.com/Jakob-Muel/neiphos2k26-timetable
cd neiphos2k26-timetable
```

2. Install dependencies:

```bash
yarn install
```

3. Clone the timetable data into `./src/lib/data`

```bash
git clone https://github.com/Jakob-Muel/neiphos2k26-timetable-data ./src/lib/data
```

4. Start the development server:

```bash
yarn dev
```

5. Open [http://localhost:5173](http://localhost:5173) in your browser

## Content Management

The application uses Sveltia CMS for content management with the timetable data located in an external repo ([neiphos2k26-timetable-data](https://github.com/Jakob-Muel/neiphos2k26-timetable-data)). This allows access to be granted to third parties (e.g. event organisers) to maintain the schedule content specifically.

Access the admin interface at `/admin` to:

- Add/edit stages and their schedules
- Set festival information

Sveltia commits directly to the Git repository via the GitHub API.

## Deployment

The app deploys automatically to GitHub Pages via the `Deploy to GitHub Pages` workflow (`.github/workflows/deploy.yml`) on every push to `main`. The workflow clones the timetable data, builds the site, and publishes it.

To build manually, both this app repo and the timetable data repo need to be present before building. The timetable repo URL is set through the `PUBLIC_TIMETABLE_REPO` environment variable, and the deployment base path through `BASE_PATH`:

```bash
export PUBLIC_TIMETABLE_REPO=https://github.com/Jakob-Muel/neiphos2k26-timetable-data
export BASE_PATH=/neiphos2k26-timetable
chmod +x ./clone-timetable-repo.sh && ./clone-timetable-repo.sh && corepack enable && yarn && yarn build
```

The `build` directory can then be served through any static hosting service.
