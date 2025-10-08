# GitHub Pages Site (Jekyll)

This directory contains a self‑contained Jekyll site ready for GitHub Pages.

## Prerequisites (WSL/Ubuntu)

- Ruby 3.x, Bundler, build tools:
  ```bash
  sudo apt-get update -y
  sudo apt-get install -y ruby-full build-essential zlib1g-dev
  ```

## Building Environment from Scratch on WSL

### Complete Setup Guide

If you're starting with a fresh WSL installation, follow these steps to set up the complete development environment:

#### 1. Update WSL and Install Essential Packages
```bash
# Update package lists
sudo apt-get update -y

# Install essential build tools and dependencies
sudo apt-get install -y curl wget git build-essential zlib1g-dev libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common apt-transport-https ca-certificates gnupg lsb-release
```

#### 2. Install Ruby (Latest Stable Version)
```bash
# Install Ruby using rbenv (recommended for version management)
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-installer | bash

# Add rbenv to your shell profile
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc

# Reload your shell configuration
source ~/.bashrc

# Install Ruby dependencies
sudo apt-get install -y libssl-dev libreadline-dev zlib1g-dev

# Install latest stable Ruby (3.2.x)
rbenv install 3.2.0
rbenv global 3.2.0

# Verify installation
ruby --version
```

#### 3. Install Bundler and Configure Gem Environment
```bash
# Install Bundler
gem install bundler

# Configure gem installation path (avoid sudo)
echo 'export GEM_HOME="$HOME/.local/share/gem"' >> ~/.bashrc
echo 'export PATH="$HOME/.local/share/gem/ruby/3.2.0/bin:$PATH"' >> ~/.bashrc

# Reload shell configuration
source ~/.bashrc

# Verify gem environment
gem env
```

#### 4. Clone and Setup the Project
```bash
# Navigate to your projects directory
cd /mnt/c/Users/amire/Desktop/projects/

# Clone the repository (if not already present)
git clone <your-repo-url> gh_site
cd gh_site

# Configure bundler to use local vendor directory
bundle config set --local path 'vendor/bundle'

# Install all dependencies
bundle install
```

#### 5. Verify Installation
```bash
# Check Ruby version
ruby --version

# Check Bundler version
bundle --version

# Check Jekyll installation
bundle exec jekyll --version

# Test the site builds correctly
bundle exec jekyll build
```

#### 6. Start Development Server
```bash
# Start the development server with live reload
bundle exec jekyll serve --host 127.0.0.1 --port 4001 --livereload --incremental

# Open in browser: http://127.0.0.1:4001
```

### Troubleshooting Common WSL Issues

#### Permission Issues
```bash
# If you encounter permission errors with gems
sudo chown -R $USER:$USER ~/.local/share/gem
```

#### Port Access from Windows
```bash
# If you can't access the site from Windows browser
# Make sure to use 127.0.0.1 or 0.0.0.0 as host
bundle exec jekyll serve --host 0.0.0.0 --port 4001 --livereload
```

#### Memory Issues
```bash
# If Jekyll build fails due to memory constraints
export JEKYLL_ENV=development
bundle exec jekyll serve --host 127.0.0.1 --port 4001 --livereload --incremental --limit_posts 10
```

### Environment Variables (Optional)
Create a `.env` file in the project root for custom configurations:
```bash
# .env file
JEKYLL_ENV=development
BUNDLE_PATH=vendor/bundle
```

## Install dependencies

```bash
cd gh_site
export PATH="$HOME/.local/share/gem/ruby/3.2.0/bin:$PATH"  # if using user gems
bundle config set --local path 'vendor/bundle'
bundle install
```

## Run locally

### Quick Development (Recommended)
```bash
bundle exec jekyll serve --host 127.0.0.1 --port 4001 --livereload --incremental
# open http://127.0.0.1:4001
```

**Features:**
- **Auto-reload**: Browser refreshes automatically when you edit any file
- **Incremental builds**: Only rebuilds changed files (faster)
- **JSON updates**: Edit `assets/projects.json` or `assets/publications.json` and see changes instantly

### Basic Development
```bash
bundle exec jekyll serve --host 127.0.0.1 --port 4000
# open http://127.0.0.1:4000
```

Notes:
- If port 4000 is busy, append `--port 4001`.
- For manual refresh only, omit `--livereload --incremental`.

## Deploy to GitHub Pages

Option A: User/organization site
- Create a repo named `<your-username>.github.io`.
- Copy the contents of `gh_site/` into the repo root and push to `main`.

Option B: Project site
- Keep `gh_site/` in your repo.
- In GitHub → Settings → Pages:
  - Source: `Deploy from a branch`
  - Branch: your default branch, Folder: `/gh_site`

## Customize

### Content Management
- **Projects**: Edit `assets/projects.json` - changes appear instantly with auto-reload
- **Publications**: Edit `assets/publications.json` - changes appear instantly with auto-reload
- **Main content**: Edit `index.html` (uses `_layouts/default.html`)
- **Styling**: Edit `css/style.css`
- **Images**: Replace/add images in `assets/images/`

### Development Workflow
1. Start server: `bundle exec jekyll serve --host 127.0.0.1 --port 4001 --livereload --incremental`
2. Edit any file (JSON, CSS, HTML)
3. Save → Browser auto-refreshes → See changes instantly!
4. No server restart needed

## License
MIT (adjust as needed).
