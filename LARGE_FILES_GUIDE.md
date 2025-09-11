# 📦 Large Files Management with Git LFS

This repository uses **Git Large File Storage (LFS)** to efficiently handle large media assets like videos and high-resolution images.

## 🎯 Why Git LFS?

- **File Size Limits**: GitHub has a 100MB file size limit for regular files
- **Repository Performance**: Large files slow down clone/fetch operations
- **Storage Efficiency**: LFS stores large files separately, keeping the repository lightweight

## 📁 Files Tracked by LFS

The following file types are automatically tracked by Git LFS (configured in `.gitattributes`):

### Video Files
- `*.mp4` - Primary video format
- `*.mov` - QuickTime videos
- `*.avi` - AVI videos
- `*.mkv` - Matroska videos
- `*.webm` - WebM videos

### Image Files
- `*.png` - PNG images
- `*.jpg` / `*.jpeg` - JPEG images
- `*.gif` - GIF images
- `*.webp` - WebP images
- `*.bmp` - Bitmap images
- `*.tiff` - TIFF images
- `*.psd` - Photoshop files

### Archive Files
- `*.zip` - ZIP archives
- `*.tar.gz` - Compressed archives
- `*.rar` - RAR archives
- `*.7z` - 7-Zip archives

### Documents
- `*.pdf` - PDF documents

## 🚀 How to Add Large Files

### 1. Regular Git Workflow (Recommended)
```bash
# Add your large files normally
git add projects/new-project/large-video.mp4
git add projects/new-project/high-res-image.png

# Commit as usual
git commit -m "Add new project media assets"

# Push to remote
git push origin main
```

Git LFS will automatically handle these files based on the `.gitattributes` configuration.

### 2. Manual LFS Tracking (If Needed)
```bash
# Track specific files manually
git lfs track "*.mp4"
git lfs track "projects/**/*.png"

# Add and commit the .gitattributes changes
git add .gitattributes
git commit -m "Update LFS tracking patterns"
```

## ✅ Verifying LFS Setup

### Check LFS-tracked Files
```bash
git lfs ls-files
```

### Check File Status
```bash
git lfs status
```

### Verify LFS Configuration
```bash
git lfs env
```

## 📤 Uploading Guidelines

### File Size Recommendations
- **Videos**: Up to 500MB each (GitHub LFS free tier limit)
- **Images**: Up to 50MB each for optimal performance
- **Total Repository**: Monitor LFS storage usage on GitHub

### Best Practices
1. **Compress Videos**: Use modern codecs (H.264/H.265) for optimal compression
2. **Optimize Images**: Use appropriate formats and compression levels
3. **Organize Files**: Keep media in project-specific folders
4. **Check Sizes**: Use `ls -lh` to verify file sizes before committing

## 🔧 Troubleshooting

### If LFS Files Don't Upload
```bash
# Ensure LFS is installed
git lfs --version

# Install LFS hooks
git lfs install

# Force push LFS files
git lfs push --all origin main
```

### If Files Are Too Large
```bash
# Check current LFS usage
git lfs ls-files -s

# Remove large files from LFS if needed
git lfs untrack "*.ext"
```

### Migrate Existing Large Files
```bash
# If you have existing large files not in LFS
git lfs migrate import --include="*.mp4,*.png" --everything
```

## 📊 Current Repository Stats

- **Total Projects**: 3 (packaroo, portfolio, portfolio admin site)
- **Video Files**: 3 files (~290MB total)
- **Image Files**: ~40 files
- **All large files are now tracked by Git LFS** ✅

## 🔗 Useful Commands

```bash
# Clone repository with LFS files
git clone https://github.com/damoiskii/portfolio-snaps.git
cd portfolio-snaps
git lfs pull

# Check LFS storage usage
git lfs ls-files -s | awk '{sum+=$1} END {print "Total LFS storage: " sum/1024/1024 " MB"}'

# List largest LFS files
git lfs ls-files -s | sort -nr | head -10
```

---

⚠️ **Important**: After the LFS migration, the git history has been rewritten. You'll need to force push to update the remote repository:

```bash
git push --force-with-lease origin main
```

This ensures your large media files will upload efficiently to GitHub! 🎉
