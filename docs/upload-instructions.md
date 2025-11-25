	# How to Upload This Documentation to GitHub

## Step 1: Prepare Your Files

You have a documentation package with this structure:

```
krs-correspondentbanking-system-modernization/
├── README.md
├── ARCHITECTURE.md
├── bounded-contexts/
├── diagrams/
└── docs/
```

## Step 2: Go to Your GitHub Repository

1. Open your browser
2. Go to: https://github.com/StigKorsholm/personal-site
3. Make sure you're signed in

## Step 3: Upload via GitHub Web Interface

### Method: Upload Folder-by-Folder

**Upload Root Files:**
1. In your repo, click "Add file" → "Upload files"
2. Create these files by clicking "Add file" → "Create new file":
   - Type filename: `architecture/krs-correspondentbanking-system-modernization/README.md`
   - Copy/paste the content from your local README.md
   - Commit the file
   - Repeat for ARCHITECTURE.md

**Upload Bounded Contexts:**
1. Click "Add file" → "Create new file"
2. Type: `architecture/krs-correspondentbanking-system-modernization/bounded-contexts/README.md`
3. Copy/paste content
4. Repeat for each Canvas document

**Upload Diagrams:**
1. Same process
2. Create files under `architecture/krs-correspondentbanking-system-modernization/diagrams/`

## Step 4: Verify Upload

1. Navigate to: `https://github.com/StigKorsholm/personal-site/tree/main/architecture/krs-correspondentbanking-system-modernization`
2. Check all folders appear
3. Click ARCHITECTURE.md - Mermaid diagrams should render
4. Click on .mmd files - they should render too

## Step 5: Share the Link

Your documentation is now live at:
`https://github.com/StigKorsholm/personal-site/tree/main/architecture/krs-correspondentbanking-system-modernization`

Share this in your LinkedIn posts! 🎉

---

## Alternative: Using Git Desktop (Easier for Beginners)

1. Download GitHub Desktop: https://desktop.github.com/
2. Clone your repository
3. Copy the entire `krs-correspondentbanking-system-modernization` folder into your local repo
4. In GitHub Desktop:
   - You'll see all new files
   - Add commit message: "Add architecture documentation"
   - Click "Commit to main"
   - Click "Push origin"
5. Done! Much easier than web interface for many files.
