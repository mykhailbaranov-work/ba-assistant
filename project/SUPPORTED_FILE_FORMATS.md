# Source File Formats

Any file type may be stored under `source/`. The project may read and analyze only content that is technically available in the active environment. The following formats are commonly readable but are not guaranteed when a required parser, application, permission, decryption key, or extraction capability is unavailable.

## Microsoft 365 and Microsoft Office

### Word

`.doc`, `.docx`, `.docm`, `.dot`, `.dotx`, `.dotm`

### Excel

`.xls`, `.xlsx`, `.xlsm`, `.xlsb`, `.xlt`, `.xltx`, `.xltm`, `.csv`

### PowerPoint

`.ppt`, `.pptx`, `.pptm`, `.pot`, `.potx`, `.potm`, `.pps`, `.ppsx`, `.ppsm`

### Outlook and mail exports

`.msg`, `.eml`

### OneNote

`.one`, `.onepkg`

### Visio

`.vsd`, `.vsdx`, `.vsdm`, `.vss`, `.vssx`, `.vst`, `.vstx`

### Project

`.mpp`, `.mpt`

### Access

`.mdb`, `.accdb`, `.accde`

### Publisher

`.pub`

## Other Supported Sources

### Documents and structured text

`.pdf`, `.txt`, `.md`, `.rtf`, `.json`, `.xml`, `.yaml`, `.yml`

### Images and screenshots

`.png`, `.jpg`, `.jpeg`, `.gif`, `.bmp`, `.tif`, `.tiff`, `.webp`

Screenshots may also be supplied directly as image attachments without a filename extension.

## Reading Rules

- Treat all supplied files as read-only source material unless the user explicitly requests a modification.
- Extract and use only content that is actually visible or readable.
- Preserve the source path, filename, and relevant page, sheet, slide, or image location when reporting material findings.
- If a file is encrypted, truncated, corrupted, unsupported in the current context, or only partially readable, state the limitation.
- Request an accessible copy, export, screenshot, or extracted text before relying on unavailable content for a final result.
- Do not infer missing content from a filename, file extension, or binary header.
- If a selected file cannot be read, report the limitation, show the available source-file list again, and request another file or a readable export or attachment.

## Generated Documents

The formats above describe readable source material. Generated outputs follow `.github/agent-rules/document-output.md`:

- use an available document-generation MCP for DOCX;
- otherwise create Markdown;
- do not install document-generation dependencies;
- keep generated outputs below `results/`, separate from read-only source documents.
