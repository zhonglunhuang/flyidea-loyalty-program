# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a design asset management project for a food ordering app. It contains 59 design mockup images that have been organized, deduplicated, and converted into documentation formats (PDF, DOCX, Markdown).

The project includes Python scripts for processing design images and generating specification documents.

## Commands

### Python Environment

This project uses a Python 3 virtual environment located at `.venv/`:

```bash
# Activate virtual environment
source .venv/bin/activate

# Install dependencies (if needed)
pip install python-docx
```

### Generate Documentation

```bash
# Convert Markdown to DOCX (single column layout)
python3 convert_to_docx.py

# Convert Markdown to DOCX (grid layout with 3 images per row)
python3 convert_to_docx_grid.py
```

### Image Processing

```bash
# Process images: find duplicates and create mapping file
python3 process_images.py

# Rename images based on mapping (already completed)
python3 rename_images.py
```

## Architecture

### Script Organization

The project has 4 main Python scripts with distinct responsibilities:

1. **process_images.py**: Image management utility
   - Scans directory for duplicate images using MD5 hashing
   - Creates `image_mapping.json` for manual categorization
   - Optionally deletes duplicates and logs to `removed_files.log`

2. **rename_images.py**: Batch file renaming
   - Contains hardcoded mapping data for 59 images
   - Renames files to format: `序號_功能_頁面_原始檔名.jpg`
   - Categories include: 點數分潤, 商品瀏覽, 購物車, 訂單交易, etc.

3. **convert_to_docx.py**: Markdown to DOCX converter
   - Parses Markdown with images, headings, tables, lists
   - Uses python-docx to generate formatted Word documents
   - Images are displayed at 5.5 inches width, center-aligned
   - Input: `功能規格文件_含圖片.md` → Output: `功能規格文件.docx`

4. **convert_to_docx_grid.py**: Grid layout variant
   - Similar to convert_to_docx.py but arranges images in table grid
   - Default: 3 images per row with captions
   - Images are smaller (calculated based on `images_per_row`)
   - Output: `功能規格文件_網格版.docx`

### Document Conversion Flow

Both DOCX converters share similar architecture:
- Read Markdown line by line with state machine parsing
- Handle headings (# ## ### ####), images (![]), tables (|), lists (- *)
- Apply Chinese font (Microsoft JhengHei) for proper rendering
- Resolve relative image paths from Markdown file location

**Key difference**: `convert_to_docx.py` renders images sequentially, while `convert_to_docx_grid.py` collects consecutive images and flushes them into grid tables.

### Image Naming Convention

All 59 images follow this pattern:
```
{序號}_{功能}_{頁面}_{原始檔名}
```

Example: `001_點數分潤_回饋金收入明細_LINE_ALBUM_樣式_251016_1.jpg`

### File Dependencies

- `功能規格文件_含圖片.md`: Source Markdown (contains image references)
- `image_mapping.json`: Image categorization metadata (11KB)
- `圖片分類清單.csv`: Excel-compatible image catalog
- `removed_files.log`: Record of 2 deleted duplicate files
- All 59 .jpg files in root directory

## Important Notes

- The virtual environment already has `python-docx==1.2.0` installed
- Image paths in Markdown are relative and resolved at runtime
- The project does NOT use Pillow - image dimensions are read using raw binary parsing (JPEG/PNG headers)
- All scripts use UTF-8 encoding for Chinese language support
- Tables in generated DOCX use "Light Grid Accent 1" style with blue headers (#4472C4)
