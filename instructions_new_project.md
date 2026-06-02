# Starting a New Project with Gald3r (OpenClaw)

Set up a brand-new project with gald3r pre-installed for **OpenClaw**.

For an existing project, see [instructions_existing_project.md](./instructions_existing_project.md).

---

## Step 1 - Get this repo

```bash
git clone https://github.com/wrm3/gald3r_platform_openclaw.git
```

Or download the ZIP from GitHub (**Code -> Download ZIP**) and unzip it.

---

## Step 2 - Copy the `openclaw/` contents into your new project

**bash / macOS / Linux:**
```bash
mkdir my-new-project
cp -r gald3r_platform_openclaw/openclaw/. my-new-project/
cd my-new-project
```

**Windows PowerShell:**
```powershell
New-Item -ItemType Directory my-new-project
Copy-Item -Recurse -Force .\gald3r_platform_openclaw\openclaw\* .\my-new-project\
Set-Location .\my-new-project
```

---

## Step 3 - Open in OpenClaw

Open the project folder in OpenClaw. gald3r auto-loads on first launch.

---

## Step 4 - Verify

In OpenClaw, type `@g-status` -- you should see a gald3r session-context block.

---

*Full docs: [README.md](./README.md) | [CHANGELOG.md](./CHANGELOG.md) | [all 34 tools](https://github.com/wrm3/gald3r)*
