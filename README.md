<p align="center"><img src="web/scribble-bridge-logo.png" alt="Scribble Bridge" width="480"></p>

# Scribble Bridge

Turn handwritten notes into editable text while preserving their layout, tables,
margin notes and connections. Compare the source with both faithful **as-written**
text and a separate **readable** expansion, then approve words and structure yourself.

Build reusable **writer/style profiles** from examples you have checked. You can use
a larger model to prepare shareable samples, correct its output, then carry the
reviewed examples and profile to a local vision model for future notes. Profiles
supply instructions and evidence; they do not retrain the model.

![Scribble Bridge showing a fictional garden-notebook project](design/browser-validation/scribble-bridge-home-wide.png)

*Application preview with synthetic notes; no personal collection is included.*

## Start on Windows

For the **Windows portable ZIP**, extract the whole ZIP and double-click
**Start-Local-Notes.cmd**. It includes Node and the image/PDF libraries, opens your
browser automatically, and needs no setup commands or first-launch download.
Keep its launcher window open while using the app. This package targets Windows
x64; ARM64 and 32-bit packages are not provided.

Portable review builds are downloadable from the **ScribbleBridge-Windows-x64**
artifact of a successful [Windows portable package workflow](https://github.com/dannyshields-AI-commits/note-topology-review/actions/workflows/windows-portable.yml).
Extract the enclosed application ZIP. GitHub's **Code → Download ZIP** is the
source package and still uses the following developer setup:

1. Install **Node.js 22.13 or newer** from [nodejs.org](https://nodejs.org/).
2. Download the application ZIP from GitHub and **extract it**. Open the extracted
   application folder where you can see the `adapters`, `workspace` and `design` folders
   and the `README` file.
3. In that folder, right-click an empty area and choose **Open in Terminal**.
   Alternatively, open PowerShell and `cd` to that folder. Reopen Terminal if Node
   was just installed. Run:

```powershell
npm.cmd ci
node workspace/start.mjs
```

`npm.cmd ci` installs PDF dependencies once for this download; repeat it after a
dependency update. The second command opens the app at **http://127.0.0.1:8768**.
No Python or AI account is needed to import or review notes. Keep Terminal open;
Ctrl+C stops the app. Next time, run only `node workspace/start.mjs`.

See [startup help](LOCAL_WORKSPACE.md#windows-startup-help) for blocked commands,
PDF checks and other platforms.

## Your first project

1. Create a project in **Home**, or choose **Import project ZIP** to restore one.
2. Create a profile in **Handwriting profiles** whenever you are ready, even before
   importing. A profile describes a writer and writing style; folders organize
   subjects, books or chapters.
3. In **Import**, choose a folder and add PNG, JPEG (`.jpg`/`.jpeg`), WebP or PDF
   files. HEIC/HEIF, TIFF, GIF and BMP need conversion to PNG or JPEG first;
   changing the filename extension is not conversion. Folder import uses the
   same supported formats. [Import details](LOCAL_WORKSPACE.md#supported-imports).
4. To transcribe, connect to an image-capable model, choose a profile, select pages
   and preview the request, including any missing writer/style labels to assign. Existing notes can be edited
   without an AI connection.
5. In **Editing**, compare source and text, correct them and save. Verify
   **as-written**, **readable** and **structure** independently. All three checks
   are needed before a page can become a recognition example.
6. **Export project** saves your notes, profiles, originals and history as a ZIP.
   Use **Import project ZIP** to move it to another computer.

[How review and profiles work](HOW_IT_WORKS.md) covers wording, chunks, connectors,
comments and approval behavior. [Local workspace help](LOCAL_WORKSPACE.md) covers
model connections, references, profile transfer and recovery.

## Choose where processing happens

Projects start with **Local models only**. Ollama needs a downloaded vision-capable
model on this PC or an authorized private LAN/Tailscale computer. The app does not
download models. **Find available models** helps identify image-capable choices.

Codex and OpenRouter require **Cloud processing allowed**. Included images,
examples, references, prompts and comments are then sent to that provider; using a
local review app does not make that request private to your PC. Use shareable
samples when building a cloud-assisted profile. The connection preview shows what
will be sent. [Connection and privacy details](LOCAL_WORKSPACE.md#choose-your-ai).

## Keep your work

Start with **Export project** and store the ZIP somewhere private. It can contain
original scans, wording, comments, profile instructions and model-run history.
**Export profile + examples** transfers a reusable reviewed profile; inspect its
contents before sharing. Neither export contains active credentials.

Saved projects live in `.private/workspace/` beside the application. Export them or
back up that directory **before replacing the application folder**. Updating or
cloning the application does not synchronize your notes. Keep personal files and
exports outside application Git. An optional separate private GitHub backup is
covered in [BACKUP.md](BACKUP.md); easier guided setup remains on the
[roadmap](TODO.md).

## For contributors

Use [EDITING.md](EDITING.md), [CLOUD_WORKFLOW.md](CLOUD_WORKFLOW.md) and
[HANDOFF.md](HANDOFF.md) for development, checks, compatibility and pull requests.
[SCHEMA.md](SCHEMA.md) describes the document format;
[EVALUATION.md](EVALUATION.md) describes controlled accuracy comparisons.
[TODO.md](TODO.md) lists future work, and [design records](design/README.md)
collect request specifications and validation evidence.

Application code is covered by the [MIT License](LICENSE). The license does not
change repository visibility or authorize sharing private notes, accounts or reviews.
