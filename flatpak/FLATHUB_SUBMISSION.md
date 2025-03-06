# Submitting UsTaxes to Flathub

This guide provides step-by-step instructions for submitting UsTaxes to Flathub.

## Prerequisites

Before submitting to Flathub, ensure you have:

1. A GitHub account
2. Git installed on your system
3. Basic familiarity with Git and GitHub
4. Tested the Flatpak package locally (see [README.md](README.md))

## Submission Process

### 1. Fork the Flathub Repository

1. Go to [https://github.com/flathub/flathub](https://github.com/flathub/flathub)
2. Click the "Fork" button in the top-right corner
3. Clone your forked repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/flathub.git
   cd flathub
   ```

### 2. Create a New Branch

Create a new branch for your submission:

```bash
git checkout -b add-ustaxes
```

### 3. Create the Application Directory

Create a directory for UsTaxes:

```bash
mkdir -p com.ustaxes.UsTaxes
```

### 4. Prepare the Manifest

Copy the manifest file and any other necessary files to the application directory:

```bash
cp /path/to/UsTaxes/com.ustaxes.UsTaxes.yml com.ustaxes.UsTaxes/
```

For Flathub submission, you'll need to modify the manifest to use a Git source instead of a local directory. Edit `com.ustaxes.UsTaxes.yml` to replace the `sources` section:

```yaml
sources:
  - type: git
    url: https://github.com/ustaxes/UsTaxes.git
    tag: v0.1.23 # Use the appropriate version tag
    commit: abcdef123456789 # Replace with the actual commit hash for the tag
```

### 5. Add AppStream Metadata

Copy the AppStream metadata file:

```bash
mkdir -p com.ustaxes.UsTaxes/metainfo
cp /path/to/UsTaxes/flatpak/com.ustaxes.UsTaxes.metainfo.xml com.ustaxes.UsTaxes/metainfo/
```

### 6. Add Screenshots

Ensure you have at least one screenshot in the AppStream metadata. Add the screenshots to your repository and update the paths in the metadata file.

### 7. Commit and Push Your Changes

```bash
git add com.ustaxes.UsTaxes
git commit -m "Add UsTaxes"
git push origin add-ustaxes
```

### 8. Create a Pull Request

1. Go to your forked repository on GitHub
2. Click "Compare & pull request"
3. Fill out the pull request template with information about UsTaxes
4. Submit the pull request

### 9. Respond to Review Feedback

The Flathub maintainers will review your submission and may request changes. Be prepared to address their feedback and make necessary adjustments.

### 10. After Approval

Once your submission is approved and merged, your application will be available on Flathub!

## Maintenance

After your application is on Flathub, you'll need to maintain it:

1. Update the manifest when new versions are released
2. Submit pull requests to the [flathub/com.ustaxes.UsTaxes](https://github.com/flathub/com.ustaxes.UsTaxes) repository (which will be created after your initial submission is accepted)

## Additional Resources

- [Flathub Documentation](https://docs.flathub.org/)
- [Flatpak Documentation](https://docs.flatpak.org/)
- [Flathub App Submission Guidelines](https://github.com/flathub/flathub/wiki/App-Submission)
- [AppStream Metadata Guidelines](https://docs.flatpak.org/en/latest/freedesktop-quick-reference.html#appstream-metadata)
