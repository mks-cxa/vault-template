# Your Second Brain: setup guide

This repository is an empty template for a personal "second brain": an Obsidian vault that Claude and
ChatGPT can read and write for you through the **Vault MCP** connector. Your notes live in your own
private GitHub repository. Nobody else can see them.

The setup takes about 30 minutes. Do the steps in order.

## 1. GitHub account

Create a GitHub account at https://github.com/signup with your work email, or use the one you have.
Turn on two-factor authentication: click your picture (top right), **Settings**,
**Password and authentication**, **Enable two-factor authentication**.

## 2. Make your own copy of this template

1. At the top of this page click **Use this template**, then **Create a new repository**.
2. **Owner:** your own account. **Repository name:** `secondbrain`.
3. Choose **Private**. This matters: your notes must not be public.
4. Click **Create repository**.

## 3. Tell Michal your GitHub username

Send Michal your GitHub username (shown when you click your picture, top right). He adds you to the
member list of the Vault MCP service and tells you when that is done.

## 4. Give the Vault MCP access to your repository

Wait until Michal confirms step 3. Then:

1. Open https://github.com/apps/vault-mcp-vaults/installations/new.
2. Choose your account.
3. Choose **Only select repositories** and pick `secondbrain`. Nothing else.
4. Click **Install**.

The app can now read and write that one repository, and nothing else in your account.

## 5. Laptop: Obsidian and the Git plugin

1. Install **Obsidian** (https://obsidian.md) and **GitHub Desktop** (https://desktop.github.com).
2. In GitHub Desktop, sign in with your GitHub account, then **File**, **Clone repository**, pick
   `secondbrain` and choose a folder, for example `Documents/secondbrain`.
3. In Obsidian: **Open folder as vault** and pick that folder.
4. Obsidian asks whether to trust the vault's plugins: choose **Trust author and enable plugins**.
5. **Settings**, **Community plugins**, **Browse**, search **Git** (by Vinzent), **Install**, then
   **Enable**. The settings come with the template: it fetches changes every minute and saves and
   uploads your edits 2 minutes after you stop typing.

Leave Obsidian open while you work. Notes Claude writes appear in it within a minute or two.

## 6. Phone or tablet (optional)

Use an **Obsidian Sync** subscription to see the vault on your phone or tablet. Your laptop is the
bridge between Sync and GitHub, so it must be switched on with Obsidian open for changes to flow.
**Never install the Git plugin on a phone or tablet**: two devices pushing to GitHub cause conflicts.

## 7. Connect Claude and ChatGPT

**Claude:** **Settings**, **Connectors**, **Add custom connector**. Name it `Vault MCP` and enter the URL

```
https://vault-mcp-551091705251.europe-west6.run.app/mcp
```

Click **Connect** and sign in with your GitHub account. If your Claude account belongs to a Team or
Enterprise organisation and you cannot add a connector, ask your organisation's owner to add it first.

**ChatGPT:** **Settings**, **Apps** (or **Connectors**), add a custom connector with the same URL and
sign in with GitHub. Custom connectors may require Developer Mode on your plan.

## 8. Teach Claude and ChatGPT to use the vault

Paste this standing instruction once.

- **Claude:** open a normal chat (outside any project) and send "Remember this as a standing
  preference for all chats:" followed by the text below. Check **Settings**, **Memory** shows it.
- **ChatGPT:** **Settings**, **Personalization**, **Custom instructions**, paste the text below.

> Second brain = my Obsidian vault via the Vault MCP connector. Write ONLY with its tools.
> Start: if the task is about my work, companies, clients, projects or people, call memory_index first, then read the relevant project hub. Skip for generic questions.
> End: save durable results without asking: decisions and the reason; facts (projects, clients, people's roles, systems, repos, URLs); learnings (what failed, fixes); project status changes. Not: chat summaries, drafts, suggestions I did not adopt, secrets, private matters.
> Ideas: idea_add. Facts and rules: memory_save (vault_read first if the memory exists). Unsure: inbox_append. Other notes: vault_read then note_write. Prefer new files; in shared files change single lines. On "file changed since read", re-read and redo.
> Never git commit, push or pull.
> Last line of work replies: "Vault: saved <what>" or "Vault: nothing".

## 9. Test it

1. In a new Claude chat, write: `call memory_index`. Claude shows the (still empty) index of your vault.
2. Then write: `add an idea: test`. Claude saves it with `idea_add`.
3. Open your `secondbrain` repository on GitHub: the newest commit is "mcp: idea_add ..." by
   "Vault MCP for <your name>", and `portfolio/ideas/` holds the new idea. Within two minutes it also
   appears in Obsidian.

If sign-in shows "This GitHub account is not allowed to use this vault.", Michal has not added you yet (step 3). If it says
"Vault app not installed on ...", redo step 4.

## 10. Privacy

- The Vault MCP server runs in Michal's Google Cloud project. For each call it logs only the tool
  name, the file path, your GitHub username, the status and the time. It never logs what your notes say.
- Your repository stays yours. The server can reach only the repository you selected in step 4.
- You can stop it at any time: on GitHub, **Settings**, **Applications**, **Installed GitHub Apps**,
  **Vault MCP Vaults**, **Uninstall**. Remove the connector in Claude and ChatGPT as well.

## What is in this template

| Folder | What goes there |
|---|---|
| `memory/` | `MEMORY.md`, the index Claude reads first; lasting facts, one per file |
| `memory/projects/` | one folder per project with a hub note |
| `memory/reference/` | facts about systems, people's roles, links |
| `memory/feedback/` | rules for how the AI works with you, and their change register |
| `notes/` | longer notes |
| `inbox/` | quick captures to sort later |
| `portfolio/ideas/` | ideas, one file each (`idea_add`) |
| `sources/` | source material a rule rests on |
