# Microsite Project

This microsite is built using Hugo, a fast and flexible static site generator. Below are the details regarding the project structure and setup.

## Project Structure

- **archetypes/**: Contains templates for new content types.
  - **default.md**: Default template for new content files.
  
- **assets/**: Contains styles and other assets.
  - **styles/**: Directory for stylesheets.
    - **main.scss**: Main SCSS file for styling the microsite.
  
- **config.toml**: Main configuration file for the Hugo site, defining site-wide settings.

- **content/**: Contains the content for the site.
  - **_index.md**: Homepage content.
  - **pages/**: Directory for additional pages.
    - **about.md**: Content for the "About" page.

- **layouts/**: Contains templates for rendering content.
  - **_default/**: Default templates.
    - **baseof.html**: Base template structure.
    - **single.html**: Template for single content pages.
  - **partials/**: Contains reusable HTML components.
    - **footer.html**: Footer HTML.
    - **header.html**: Header HTML.

- **package.json**: Configuration file for npm, listing dependencies and scripts.

- **static/**: Contains static files served directly to the client.
  - **fonts/**: Directory for font files.

- **themes/**: Contains custom themes.
  - **custom/**: Directory for the custom theme.
    - **layouts/**: Custom layouts for the theme.
      - **index.html**: Layout for the homepage.
    - **theme.toml**: Configuration for the custom theme.

## Setup Instructions

1. **Install Hugo**: Follow the installation instructions on the [Hugo website](https://gohugo.io/getting-started/installation/).

2. **Clone the Repository**: Clone this microsite repository to your local machine.

3. **Navigate to the Project Directory**:
   ```bash
   cd microsite
   ```

4. **Start the Hugo Server**: Run the following command to start the local development server:
   ```bash
   hugo server
   ```

5. **Access the Microsite**: Open your web browser and go to `http://localhost:1313` to view the microsite.

## Usage

- To create new content, use the archetype defined in `archetypes/default.md`.
- Modify styles in `assets/styles/main.scss` and compile them to CSS.
- Update the configuration in `config.toml` as needed for your site.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.