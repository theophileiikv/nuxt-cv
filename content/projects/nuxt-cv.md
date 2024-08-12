# Nuxt CV

A simple, minimalist CV/resume builder using Nuxt.js and YAML files for content management.

[Link to GitHub repository](https://github.com/theophileiikv/nuxt-cv/)

## Features

- Clean, minimalist design
- Content management using YAML files and Nuxt Content
- Responsive layout
- Easy to customize and extend
- Built with Nuxt.js
- Uses @nuxt/ui for consistent styling
- Separate pages for detailed project information

## Prerequisites

- Node.js (v14.x or later recommended)
- npm or yarn

## Setup

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/nuxt-cv.git
   cd nuxt-cv
   ```

2. Install dependencies:
   ```
   npm install
   # or
   yarn install
   ```

3. Update the content:
   - Edit `content/data/resume.yml` with your personal information
   - Edit `content/data/projects.yml` with your project details
   - Add or modify Markdown files in the `content` directory for detailed project information

4. Run the development server:
   ```
   npm run dev
   # or
   yarn dev
   ```

5. Open `http://localhost:3000` in your browser to see your CV.

## Customization

- Modify Vue components in the `components` directory to change the structure and layout
- Update `app.config.ts` to change the primary color theme
- Add new components or pages as needed

## Building for Production

To create a production version of your CV:

```
npm run build
# or
yarn build
```

This will generate a `dist` directory with your static site, ready for deployment.

## License

This project is open source and available under the [MIT License](https://choosealicense.com/licenses/mit/).

## Acknowledgments

- [Orginal idea from Bartosz Jarocki](https://github.com/BartoszJarocki/cv)