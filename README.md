# Your Second Brain: setup guide

For Christian, Axel and Dejan. Questions: Michal.

## What you get

A personal "second brain": an Obsidian vault (a folder of plain Markdown notes) that Claude and ChatGPT can read and write for you. When you work with the AI on your projects, it looks up what it already knows about them first and saves decisions, facts and ideas afterwards without being asked. You can read and edit the same notes yourself in Obsidian on your laptop, phone and tablet.

- Your notes live in **your own private GitHub repository**. Nobody else can see them, Michal included, unless you invite them.
- The AI reaches your vault through the **Vault MCP** connector. It is one shared service, but each person signs in with their own GitHub account and the service can only reach that person's repository.
- Only results are stored (decisions, facts, ideas, notes). Chat transcripts are never stored.

## How it fits together

```
Claude (web, desktop, iPhone, iPad, Claude Code)  ─┐
ChatGPT (web, apps, Codex)                         ├─► Vault MCP ─► your private GitHub repo "secondbrain"
                                                   ┘                       ▲
                                                                           │ Obsidian Git plugin
                                                                           │ (pulls every minute, uploads 2 min after you stop typing)
                                                                     Laptop: Obsidian
                                                                           ▲
                                                                           │ Obsidian Sync (optional, paid)
                                                                     Phone, tablet: Obsidian
```

GitHub holds the master copy and is your backup. The laptop is the bridge: it brings the AI's notes into Obsidian and uploads your own edits. Phones and tablets sync with the laptop through Obsidian Sync.

## Before you start

You need about 45 minutes and:

- a laptop (Mac or Windows) on which you can install software
- a Claude account and/or a ChatGPT account (a paid plan; see step 8)
- optional for phone and tablet: an Obsidian Sync subscription (about USD 4 to 5 per month, billed by Obsidian)

Do the steps in order. Steps 1 to 4 set up GitHub, steps 5 to 7 set up your devices, steps 8 to 10 connect the AI.

---

## Part A: GitHub

### 1. GitHub account

1. Go to https://github.com/signup and create an account with your **personal email** (not your capptoo.com address). The second brain is yours and should stay with you beyond any one company; a work address would lock you out of your own account if that mailbox ever closes. If you already have a personal GitHub account, use it.
2. Turn on two-factor authentication: click your picture (top right), **Settings**, **Password and authentication**, **Enable two-factor authentication**. Use an authenticator app.

### 2. Create your vault repository from the template

1. Open https://github.com/mks-cxa/vault-template.
2. Click **Use this template**, then **Create a new repository**.
3. **Owner:** your own account. **Repository name:** `secondbrain`.
4. Choose **Private**. This matters: your notes must never be public.
5. Click **Create repository**.

### 3. Send Michal three things

1. Your GitHub username (click your picture, top right).
2. Your repository, for example `your-username/secondbrain`.
3. Your usual time zone (for example `Europe/Zurich` or `Australia/Sydney`), so notes get the right date.

Michal adds you to the member list and tells you when that is done. Until then, sign-in shows "This GitHub account is not allowed to use this vault."

### 4. Give the Vault MCP access to your repository

Wait for Michal's confirmation from step 3, then:

1. Open https://github.com/apps/vault-mcp-vaults/installations/new.
2. Choose your account.
3. Choose **Only select repositories** and pick `secondbrain`. Nothing else.
4. Click **Install**.

The app can now read and write that one repository and nothing else in your account. You can remove it at any time (see "Privacy").

---

## Part B: Obsidian on your devices

### 5. Laptop (Mac or Windows)

The laptop needs three things: Git (the program that talks to GitHub), your vault folder, and Obsidian with the Git plugin.

**5.1 Install Git and sign it in to GitHub**

- **Mac:**
  1. Open Terminal and run `xcode-select --install`. Confirm the dialog (this installs Git). If it says it is already installed, continue.
  2. Install Git Credential Manager: download the latest `.pkg` for macOS from https://github.com/git-ecosystem/git-credential-manager/releases and run it. It lets Git sign in to GitHub through your browser.
- **Windows:**
  1. Install Git for Windows from https://git-scm.com/download/win. Keep the default options; it includes Git Credential Manager.

**5.2 Get your vault onto the laptop**

1. Install GitHub Desktop from https://desktop.github.com and sign in with your GitHub account.
2. **File**, **Clone repository**, pick `secondbrain`.
3. Choose a local folder that is **not** synced by iCloud, OneDrive or Dropbox, for example:
   - Mac: `/Users/<you>/Vaults/secondbrain` (not in Documents or Desktop if iCloud "Desktop & Documents" is on)
   - Windows: `C:\Vaults\secondbrain` (not in a OneDrive folder)
   Two sync tools on one folder cause conflicts.
4. Click **Clone**. You only need GitHub Desktop for this once.

**5.3 Obsidian and the Git plugin**

1. Install Obsidian from https://obsidian.md.
2. Start it, choose **Open folder as vault** and select the folder from 5.2.
3. Obsidian asks whether to trust the vault's plugins: choose **Trust author and enable plugins**.
4. **Settings** (gear, bottom left), **Community plugins**, **Browse**, search **Git** (by Vinzent), **Install**, then **Enable**. The settings come with the template: it fetches changes every minute and uploads your edits 2 minutes after you stop typing.
5. Recommended: **Settings**, **Core plugins**, turn on **Bases** (gives you the project and roadmap overviews).
6. First sync test: press Cmd+P (Mac) or Ctrl+P (Windows), type **Git: Commit-and-sync**, Enter. The first time, a browser window may ask you to sign in to GitHub: do it. Afterwards there should be no red error notice.

Leave Obsidian open while you work. If Obsidian is closed nothing breaks, but your laptop, phone and tablet fall behind until you open it again.

### 6. Turn on Obsidian Sync on the laptop (only if you want phone or tablet)

1. Buy Obsidian Sync (Standard is enough): https://obsidian.md/sync, with an Obsidian account.
2. In Obsidian on the laptop: **Settings**, **Sync**, log in, **Choose**, **Create new vault**. Name it `secondbrain`, region **Europe**, turn on **end-to-end encryption** and set an encryption password. Store the password in your password manager.
3. **Connect**. If it asks about merging, choose **Continue**, then **Start syncing**.
4. In **Settings**, **Sync**: turn **off** "Installed community plugins" and "Active community plugin list". This keeps the Git plugin on the laptop only.

### 7. Phone and tablet (iPhone, iPad, Android)

Install Obsidian from the App Store or Google Play, open it, and follow these screens exactly. The wording is confusing, because the vault does not exist on the device yet:

1. "Create a vault" or "Use my existing vault": tap **Create a vault**.
2. "Set up sync" or "Continue without sync": tap **Set up sync**.
3. "Obsidian Sync", "iCloud", "Other sync methods or skip": tap **Obsidian Sync**.
4. Log in with your Obsidian account.
5. "Create new sync vault" or "Choose an existing vault": tap **Choose an existing vault** and pick **secondbrain**.
6. Enter the encryption password from step 6, **Connect**, and let the first sync finish.
7. **Settings**, **Sync**: turn **off** "Installed community plugins" and "Active community plugin list" (sync settings are per device).

**Never install the Git plugin on a phone or tablet.** Only the laptop talks to GitHub; a second device doing it causes conflicts.

Test: create a note on the phone. Within about two minutes it appears on the laptop and on GitHub (laptop on, Obsidian open).

---

## Part C: Connect the AI

Connector URL for everything below:

```
https://vault-mcp-551091705251.europe-west6.run.app/mcp
```

**Sign-in tip:** the connector signs in with whatever GitHub account your browser is currently logged in to. If you use more than one GitHub account, sign out of GitHub in the browser first and sign in with the account from step 1.

### 8. Claude

**8.1 Add the connector (once, on the web)**

1. Open https://claude.ai, **Settings**, **Connectors**, **Add custom connector**.
2. Name: `Vault MCP`. URL: the connector URL above. **Add**, then **Connect**, and sign in with GitHub.
3. If your Claude account belongs to a Team or Enterprise organisation and you cannot add connectors, ask the organisation owner to add the connector first; you then only click **Connect**.
4. Recommended tool permissions (Settings, Connectors, Vault MCP): reading tools "Always allow"; `idea_add`, `inbox_append`, `note_write` "Always allow"; `memory_save` "Needs approval", because saved memories steer every future chat.

**8.2 Desktop, iPhone, iPad and Claude Code**

Nothing to add. The Claude desktop app, the iPhone and iPad apps and Claude Code (when signed in with your claude.ai account) use the same connector automatically. Do not add a second copy of it anywhere.

**8.3 Teach Claude to use the vault**

Open a normal chat **outside any project** and send:

> Remember this as a standing preference for all chats: (then paste the standing instruction from step 10)

Check under **Settings**, **Memory** that it is saved. A preference saved inside a project only applies to that project.

### 9. ChatGPT (optional)

1. ChatGPT on the web: **Settings**, **Apps & Connectors**, **Advanced settings**, turn on **Developer mode**. Developer mode needs a paid plan; in a Business or Enterprise workspace an admin may have to allow it.
2. Then **Create** (custom app or connector): name `Vault MCP`, the connector URL above, authentication **OAuth**. Leave the advanced OAuth settings as they are, confirm the risk notice, **Create**, and sign in with GitHub.
3. **Settings**, **Personalization**, **Custom instructions**: paste the standing instruction from step 10.
4. Recommended: **Settings**, **Data controls**, "Improve the model for everyone" off.
5. The app then works in every chat. If a chat answers without your vault, start the message with `@Vault MCP`.

The ChatGPT menus change often; if a label differs, look for "connectors", "apps" or "developer mode".

**Codex (optional, for developers):** sign in to Codex with "Sign in with ChatGPT" and it uses the same app; do not add the server again.

### 10. The standing instruction

Paste this into Claude (step 8.3) and ChatGPT (step 9.3):

> Second brain = my Obsidian vault via the Vault MCP connector. Write ONLY with its tools.
> Start: if the task is about my work, companies, clients, projects or people, call memory_index first, then read the relevant project hub. Skip for generic questions.
> End: save durable results without asking: decisions and the reason; facts (projects, clients, people's roles, systems, repos, URLs); learnings (what failed, fixes); project status changes. Not: chat summaries, drafts, suggestions I did not adopt, secrets, private matters.
> Ideas: idea_add. Facts and rules: memory_save (vault_read first if the memory exists). Unsure: inbox_append. Other notes: vault_read then note_write. Prefer new files; in shared files change single lines. On "file changed since read", re-read and redo.
> Never git commit, push or pull.
> Last line of work replies: "Vault: saved <what>" or "Vault: nothing".

The last line is your check: every work reply ends with "Vault: ...", so you see at a glance whether something was saved. In long chats the AI sometimes forgets; just say "save that to the vault".

---

## Part D: Test

1. New Claude chat: `call memory_index`. Claude shows the (still empty) index of your vault.
2. Then: `add an idea: test`. Claude saves it with `idea_add`.
3. On GitHub, open your `secondbrain` repository: the newest commit is `mcp: idea_add ...` by `Vault MCP for <your name>`, and `portfolio/ideas/` holds the idea.
4. Within two minutes the idea appears in Obsidian on the laptop, and shortly after on your phone and tablet.
5. Repeat step 1 in ChatGPT if you connected it.
6. Delete the test idea in Obsidian.

## Using it day to day

- **Just work normally.** Ask Claude about your projects, clients and decisions; it reads the vault first and saves results at the end.
- **Start a project:** tell Claude "create a project hub for <project>" and it sets up a folder under `memory/projects/`.
- **Capture quickly:** "inbox: <anything>" saves a note to sort later; "idea: <anything>" saves an idea.
- **Edit by hand** in Obsidian whenever you like. Avoid editing the exact note the AI is writing at the same moment.
- **The AI cannot delete, rename or move files.** Do that yourself in Obsidian.
- **Never store passwords, keys or other secrets** in the vault.
- **Client and company confidential material** (contracts, customer data, personal data of clients' customers, NDA content) does not belong in a personal vault. Keep decisions, learnings and your own working notes; link to the company system for the documents themselves.

## What is in the vault

| Folder | What goes there |
|---|---|
| `memory/MEMORY.md` | the index the AI reads first: who you are, rules, active projects |
| `memory/projects/` | one folder per project, with a hub note |
| `memory/reference/` | facts about systems, people's roles, links |
| `memory/feedback/` | rules for how the AI works with you, plus their change register |
| `notes/` | longer notes |
| `inbox/` | quick captures to sort later |
| `portfolio/ideas/` | ideas, one file each |
| `sources/` | source material a rule rests on |

## Troubleshooting

| You see | Do this |
|---|---|
| "This GitHub account is not allowed to use this vault." | Michal has not added you yet (step 3), or you signed in with another GitHub account (see the sign-in tip in Part C). |
| "Vault app not installed on ..." | Redo step 4, with `secondbrain` selected. |
| Obsidian: "Cannot run git command" or "git not found" | Git is not installed: redo step 5.1, then restart Obsidian. |
| Obsidian: push or pull fails with an authentication error | Run **Git: Commit-and-sync** once by hand and complete the GitHub sign-in in the browser. On a Mac, check that Git Credential Manager is installed (5.1). |
| AI notes do not appear in Obsidian | Is Obsidian open on the laptop, and is the laptop online? Check GitHub: if the commit is there, the laptop has not pulled yet. |
| Phone or tablet not updating | Laptop on with Obsidian open; Sync shows a green tick on both devices. |
| Obsidian: "You have conflicts in N files" | Open each file, keep the right lines, delete the marker lines (`<<<<<<<`, `=======`, `>>>>>>>`), save, then **Git: Commit-and-sync**. Ask Michal if unsure. |
| Claude or ChatGPT answers without your vault | Check the connector is connected (Settings, Connectors). In ChatGPT start with `@Vault MCP`. |

## Privacy

- The Vault MCP service runs in Michal's Google Cloud project (Zurich region). For each call it logs only the tool name, the file path, your GitHub username, the status and the time. It never logs what your notes say.
- Your repository stays yours. The service can only reach the one repository you selected in step 4, and only while you are on the member list.
- Obsidian Sync is end-to-end encrypted with your own password.
- **To stop at any time:** on GitHub, **Settings**, **Applications**, **Installed GitHub Apps**, **Vault MCP Vaults**, **Uninstall**. Remove the connector in Claude and ChatGPT as well. Your notes stay in your repository.
