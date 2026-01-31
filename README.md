# 📝 Changelog Action

A GitHub Actions workflow that generates AI-powered changelogs. It extracts commits from a date range and produces user-friendly, categorized changelogs.

Choose between two AI providers:

- 🟤 **Anthropic** (Claude Sonnet 4.5)
- 🟢 **OpenAI** (GPT-5.2)

## ⚙️ Setup

### Option 1: Anthropic (Claude)

1. Copy the workflow file to your repository:

   ```bash
   mkdir -p .github/workflows
   curl -o .github/workflows/changelog.yml https://raw.githubusercontent.com/gordysc/changelog-action/main/anthropic.yml
   ```

2. Add your API key as a repository secret:
   - Go to **Settings > Secrets and variables > Actions**
   - Click **New repository secret**
   - Name: `ANTHROPIC_API_KEY`
   - Value: Your API key from [console.anthropic.com](https://console.anthropic.com)

### Option 2: OpenAI (GPT-5.2)

1. Copy the workflow file to your repository:

   ```bash
   mkdir -p .github/workflows
   curl -o .github/workflows/changelog.yml https://raw.githubusercontent.com/gordysc/changelog-action/main/openai.yml
   ```

2. Add your API key as a repository secret:
   - Go to **Settings > Secrets and variables > Actions**
   - Click **New repository secret**
   - Name: `OPENAI_API_KEY`
   - Value: Your API key from [platform.openai.com](https://platform.openai.com)

## 🚀 Usage

1. Go to the **Actions** tab in your repository
2. Select **Changelog** from the workflows list
3. Click **Run workflow**
4. Fill in the inputs:
   - 📅 **Start date**: Beginning of the date range (YYYY-MM-DD)
   - 📅 **End date**: End of the date range (YYYY-MM-DD)
   - 📤 **Output type**: Choose `file` or `release`

### Output Types

- 📄 **file**: Commits the changelog to `changelogs/changelog-YYYY-MM-DD-to-YYYY-MM-DD.md` in your repository
- 🏷️ **release**: Creates a GitHub Release with the changelog as the release notes

Both options also upload the changelog as a workflow artifact for download.

## 📋 Example Output

The workflow categorizes commits into sections like:

- ✨ New Features
- 🐛 Bug Fixes
- 🔧 Improvements
- ⚠️ Breaking Changes

Only categories with relevant commits are included.

## 📦 Requirements

- Repository must have commit history (the workflow fetches full history)
- API key secret must be configured (`ANTHROPIC_API_KEY` or `OPENAI_API_KEY`)
- Workflow needs `contents: write` permission (already configured in the workflow file)

## 🎨 Customization

Edit the workflow file to customize:

- 🤖 **AI model**: Change to a different model from your chosen provider
- 💬 **Prompt**: Modify the technical writer prompt to adjust output style
- 🏷️ **Categories**: Update the category list in the prompt
- 📁 **Output location**: Change the `changelogs/` directory path

## 📄 License

MIT
