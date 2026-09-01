# Putting this online — two jobs, about twenty minutes

Both need your own Google and GitHub accounts, so neither can be done for you.
Everything else is already written.

---

## Job 1 — the Google Form (5 minutes)

This is the form testers fill in so you can add them to the closed test. Make it
first, because the site links to it.

### 1. Create it

Go to **[forms.new](https://forms.new)** while signed in as the Google account
that owns your Play Console. A blank form opens.

### 2. Paste this in

**Form title** (the big title at the top):

```
Artificial Intelligence for Everyone — Closed Testing Signup
```

**Form description** (the line under the title):

```
The companion app for the book "Artificial Intelligence for Everyone" is in closed testing on Google Play. Enter the email on your Android device's Google account below and I will add it to the tester list — you will then be able to install the app from the Play Store. Usually within a day.

The whole book offline, 24 interactive labs, 291 practice problems. No ads, no accounts, no permissions, no data collected.
```

**The question.** Click the first question and set it to:

- **Question text:**
  ```
  Your Google account email (the one signed in on your Android device)
  ```
- **Type:** *Short answer*
- **Required:** on (the toggle at the bottom right of the question)
- **Response validation:** click the ⋮ menu at the bottom right of the question
  → **Response validation** → set it to **Text · Email address**, and put this in
  the error box:
  ```
  Please enter a valid Google account email address.
  ```

> This last step matters more than it looks. Play matches testers by exact
> Google account email; a typo means the person is added to nothing and cannot
> tell why.

**A second question, optional but useful** (click ⊕ to add one):

- **Question text:**
  ```
  Anything you would like me to know? (optional)
  ```
- **Type:** *Paragraph*, not required.

### 3. Settings

Open the **Settings** tab at the top of the form:

- **Responses → Collect email addresses:** leave **off**. Turning it on forces
  testers to be signed in to Google in their browser, which puts people off, and
  you are already asking for the address in the question.
- **Responses → Limit to 1 response:** leave **off** — a household may sign up
  two phones.
- **Presentation → Confirmation message:** replace the default with:
  ```
  Thank you. Your email is on the list — I add testers in batches, usually within a day. Once you are added, open the Play Store link on the project page and install as normal. If it says the app is not available, give it a few hours and try once more.
  ```

### 4. Get the link

Click **Send** (top right) → the **🔗 link** tab → tick **Shorten URL** →
**Copy**. You get something like `https://forms.gle/AbCdEf123`.

> ### DONE — the link is already in the site
> The form is live at <https://forms.gle/nKVmZFRs8nbgZJMA9> and `index.html`
> already points **Request tester access** at it. If you ever rebuild the form,
> search `index.html` for `forms.gle` and swap the link — it appears once.

### 5. Reading the answers

In the form, the **Responses** tab lists every email. Click the green
spreadsheet icon to open them in Google Sheets — that is the list you copy into
Play Console under **Testing → Closed testing → Testers**.

---

## Job 2 — the GitHub Pages site (15 minutes)

### 1. Make the repository

On [github.com/new](https://github.com/new):

| Field | Value |
|---|---|
| Repository name | `artificial-intelligence-for-everyone` |
| Description | `Book and companion app — Artificial Intelligence for Everyone (2026)` |
| Visibility | **Public** (GitHub Pages needs public on a free account) |
| Initialise with README | **no** — this folder already has one |

The name matters: it becomes the address
`https://ismaelabdulrahman.github.io/artificial-intelligence-for-everyone/`,
and it matches the links already in `index.html` and `README.md`. If you choose
a different name, search both files for
`artificial-intelligence-for-everyone` and change it there too.

### 2. Upload this folder

The simplest way, with no Git installed:

1. On the empty repository page, click **uploading an existing file**.
2. Open this `website` folder, select **everything inside it** (not the folder
   itself) and drag it onto the page. Include the `assets` and `book` folders.
3. Commit message: `Initial site`. Click **Commit changes**.

The PDF is 21 MB. GitHub's per-file limit is 100 MB, so it is fine, but the
upload takes a minute on a slow connection. If the browser upload stalls, use
GitHub Desktop instead, or leave the PDF out for now and add it afterwards —
the site works without it, only the two download buttons will 404.

If you do use Git:

```bash
cd website
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/ismaelabdulrahman/artificial-intelligence-for-everyone.git
git push -u origin main
```

### 3. Switch Pages on

In the repository: **Settings → Pages** (left sidebar).

- **Source:** *Deploy from a branch*
- **Branch:** `main`, folder `/ (root)`
- **Save**

Wait a minute, then reload. GitHub shows the live address at the top of that
page. Your site is at:

```
https://ismaelabdulrahman.github.io/artificial-intelligence-for-everyone/
```

### 4. Check it

Open it on a phone as well as a computer. Check that the cover image appears,
the five screenshots appear, **Download the PDF** downloads the book, and
**Request tester access** opens your form.

---

## What this also solves

`store/BUILD_AND_PUBLISH.md` has a step marked **YOU MUST DO THIS (10 of 11) —
host the privacy policy**. This site does it. Once Pages is live, the URL to
paste into **Play Console → App content → Privacy policy** is:

```
https://ismaelabdulrahman.github.io/artificial-intelligence-for-everyone/privacy.html
```

Play requires a privacy policy URL even for an app that collects nothing, and it
must be reachable without signing in — a GitHub Pages URL satisfies both.

---

## Updating it later

Edit the file on GitHub (pencil icon) or push a change; Pages redeploys in about
a minute. When the app leaves closed testing, the only edits needed are in the
`testing-box` section of `index.html`: change the heading, drop the three steps,
and make the Play Store button the primary one.
