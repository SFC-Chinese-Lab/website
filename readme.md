# SFC Chinese Lab — Website

Server path: `/pub/WWW/china-lab`

## Technologies

- AI Tools
- CLI
- HTML / CSS
- Bootstrap

## Prerequisites

This document is written for people who:

- Understand basic HTML syntax
- Understand the concept of directories and file paths
- Can use the command line at a basic level (equivalent to an introductory CS course)
- Are willing to look things up and troubleshoot independently

## Updating the Site

### Process

To ensure only accurate, appropriate information is published, follow this review flow.

**(1) Clone the repo** — first time only

**(2) Get the latest main**

```bash
git fetch origin
git checkout main
git merge origin/main
```

**(3) Make your changes on a branch** — do this before editing anything

```bash
git checkout your-branch
git merge main          # bring main into your branch BEFORE editing
# (use AI or your editor to make changes)
```

**(4) Commit and push**

```bash
git commit -m "your message"
git push
```

**(5) Open a PR and request a review from your teammate**
- Assign a teammate as reviewer on the PR
- The reviewer should **approve** if everything looks correct, or **leave a comment** describing what needs to be fixed
- Address any comments, push the fixes, and re-request review
- If main receives new commits while your PR is waiting, repeat step 3 (`git merge main` on your branch, then `git push`) to keep your branch up to date

**(6) After your PR merges → go back to step 2**

### Technical Notes

- The site is managed via GitHub under the `SFC-Chinese-Lab` organization (`website` repository).
- The general workflow is: push to GitHub → SSH into the CNS shared server → `git pull`.
- A personal access token is required to authenticate `git pull` on the CNS server. Search online for setup instructions; it is a one-time setup.

If you run into technical issues, ask a knowledgeable colleague, contact the ITC help desk, or reach out to the contacts listed at the bottom of this document.

## Updating NEWS Posts

1. Add a 16:9 banner image named `yyyymmdd.jpg` to `news_img/YYYY/` (where `YYYY` is the 4-digit year of the post date).
2. Duplicate `news/template.html` and save it as `news/YYYY/yyyymmdd.html`.
3. In the new file, fill in the news title, replace `YYYY.MM.DD` with the actual date, replace `noimage.jpg` with `../../news_img/YYYY/yyyymmdd.jpg` (use `../noimage.jpg` only if no image is available — avoid this when possible), and replace the placeholder comment with the article content (use `<p>` tags for paragraphs).
4. In `news/news.html`, duplicate the `[start of article block ~ end of article block]` section and place it at the top. Update the path (e.g., `2026/20260101.html`), date (3 places), and title.
5. In `index.html` (root directory), cut the oldest article block from the "Notice" section and paste a new one at the top. Update the path, date (3 places), and title.
6. Verify that `index.html`, `news/news.html`, and `news/YYYY/yyyymmdd.html` are all correct.

**Notes:**

- If multiple articles are published on the same date, use `yyyymmdd_1.html`, `yyyymmdd_2.html`, etc. (underscore separator, not hyphen).
- To make images inside an article scale responsively to the article width, add `class="container-fluid"` to the `<img>` element.
- PDFs and supplementary images for news articles go in the appropriate subdirectory under `news_upload/` (see directory structure below).

## Semester Update Timeline

The following is a checklist of recurring homepage maintenance tasks organized by time of year. Use this as a reference at the start of each semester.

---

### (1) During Vacation — Kakyo (科挙) Announcements

These tasks occur twice a year, during winter break and summer break.

#### a. Post kakyo requirements (科挙要項掲載)

Update the kakyo page with the exam date and requirements, then publish a news post.

- Upload the requirements PDF to `news_upload/kakyo/` named `{year}{s/f}_kakyo_schedule.pdf`
- Update `pages/kakyo.html` with the new exam schedule and link to the PDF
- Create `news/YYYY/yyyymmdd.html` for the announcement
- Update `news/news.html` and `index.html`

| Semester              | Timing        |
| --------------------- | ------------- |
| Spring (winter break) | Late February |
| Fall (summer break)   | Late August   |

#### b. Post kakyo results (科挙試験結果掲載)

Publish the exam results after grading is complete.

- Upload the results PDF to `news_upload/kakyo/` named `{year}{s/f}_kakyo_result.pdf`
- Update `pages/kakyo.html` with a link to the results PDF
- Create `news/YYYY/yyyymmdd.html` for the results announcement
- Update `news/news.html` and `index.html`

| Semester              | Timing             |
| --------------------- | ------------------ |
| Spring (winter break) | Mid–late March     |
| Fall (summer break)   | Mid–late September |

---

### (2) At 教材準備会 (Teaching Materials Prep Meeting)

| Semester | Timing         |
| -------- | -------------- |
| Spring   | Early April    |
| Fall     | Late September |

#### a. Update `pages/tasa.html`

- Create a Google Form to collect each new SA's profile photo, name, year, and a one-sentence self-introduction
- Delete the outgoing SAs' entries from `tasa.html`
- Move their profile photos from `upload/tasa_profile/` to `upload/tasa_profile/archived/`
- Add entries for new SAs once form responses are collected
    - Profile photos **must be square (1:1 aspect ratio)**; save to `upload/tasa_profile/`
- Update the current semester label on the page
- Replace the lab attendance schedule (研究室駐在表) with a placeholder such as "調整中" (being finalized)

#### b. Update `pages/teachers.html`

- Similar to the TASA update above, but no Google Form is needed — the faculty will send updated information directly
- Update profile photos in `upload/teachers/` as needed
- Update the current semester label

#### c. Update `pages/study_room.html`

- Update the current semester label
- Replace the lab attendance schedule (研究室駐在表) with a "調整中" placeholder

---

### (3) Beginning of Each Semester — Week 1 or 2

- Replace the "調整中" placeholder in both `pages/tasa.html` and `pages/study_room.html` with the confirmed lab attendance schedule (研究室駐在表)
- Update the QR code on `pages/study_room.html` if the linked schedule URL has changed

---

### (4) During the Semester — News Posts

Post news articles as events occur. Typical events each semester:

| Event                    | Japanese         | Notes                                                          |
| ------------------------ | ---------------- | -------------------------------------------------------------- |
| Event overview / kickoff | イベント概要     | Posted near the start of semester                              |
| Campus tour              | キャンパスツアー | Photos →`news_upload/campustour/`                              |
| Gyoza party              | 餃子パーティー   | Photos →`news_upload/gyoza/`                                   |
| Katarukai                | 語る会         | Photos →`news_upload/kataru/`                                  |
| Sungeki taikai           | 寸劇大会         | Photos →`news_upload/sungeki/`                                 |
| Study abroad programs    | 海外研修         | Announcement only, or with photos →`news_upload/study_abroad/` |

Follow the [Updating NEWS Posts](#updating-news-posts) steps for each post.

---

## Directory Structure

```
website/
├── img/                    # Images used on permanent pages and the top page
│   ├── carousel/           # Homepage slideshow background images
│   ├── courses/            # Curriculum and course images
│   ├── favicon/            # Site favicon
│   ├── icons/              # Homepage navigation card icons
│   ├── lab/                # Language lab photos
│   ├── old/                # Outdated images kept for reference
│   ├── pronunciation/      # Pronunciation page illustrations
│   └── study_abroad/       # Study abroad page images
│
├── member/                 # Password-protected pages (see Password Protection below)
│
├── news/                   # News article pages and index
│   ├── 2022/               # Articles from 2022 (filename: yyyymmdd.html)
│   ├── 2023/               # Articles from 2023
│   ├── 2024/               # Articles from 2024
│   ├── 2025/               # Articles from 2025
│   ├── 2026/               # Articles from 2026
│   ├── news.html           # News index page (list of all articles)
│   └── template.html       # Template to copy when creating a new article
│
├── news_img/               # Thumbnail images for news articles
│   ├── 2022/ … 2026/       # Organized by year; filename format: yyyymmdd.jpg
│   ├── noimage.jpg         # Fallback thumbnail when no image is available
│   └── blank_sample.jpg    # Blank gray placeholder image
│
├── news_upload/            # Supplementary files (photos, PDFs) linked from news articles
│   ├── kakyo/              #  files; named {year}{s/f}_kakyo_schedule/result.pdf
│   ├── kataru/             # 語ろう event photos
│   ├── sungeki/            # 寸劇大会 event photos
│   ├── gyoza/              # 餃子パーティー photos
│   ├── campustour/         # Campus tour PDFs and photos
│   ├── study_abroad/       # Study abroad program flyers and photos
│   ├── events/             # General event images
│   └── tasa_boshu/         # TASA recruitment flyers
│
├── pages/                  # Permanent (non-news) content pages
│   ├── listening/          # Listening exercise pages (listening*.html)
│   ├── words/              # Vocabulary pages (words*.html)
│   └── *.html              # Other permanent pages (teachers, courses, lab, tasa, etc.)
│
├── sound_zip/              # Bulk audio download ZIP files
│                           # Current as of March 2023; corresponds to the red textbook.
│                           # Useful for students — keep this up to date if possible.
│
├── style/                  # Custom CSS overrides that could not be handled by Bootstrap alone
│
├── upload/                 # Static assets (audio files, PDFs) used by permanent pages
│   ├── class_material/     # Class handouts and materials
│   ├── grammar_worksheets/ # Grammar worksheet PDFs
│   ├── inten_sched/        # Intensive course schedule PDFs
│   ├── lab/                # Language lab reservation files
│   ├── legacy_misc/        # Legacy files inherited from the old site
│   ├── listening/          # Audio files for listening exercises
│   ├── news_assets/        # Miscellaneous assets linked from news articles
│   ├── office_docs/        # Administrative documents
│   ├── ohp_slides/         # OHP / slide files used in classes
│   ├── pronunciation/      # Audio files for pronunciation exercises
│   ├── qrcode/             # QR code images
│   ├── study_room_sched/   # Study room schedule PDFs
│   ├── tasa_profile/       # TASA member profile photos
│   │   └── archived/       # Profile photos no longer listed on the TASA page
│   ├── teachers/           # Teacher profile photos
│   ├── textbook_audio/     # Textbook companion audio files
│   └── words_audio/        # Audio files for vocabulary exercises
│
├── .gitignore              # Excludes old-site backups on the CNS server from git tracking
├── .htaccess               # Password protection and redirect rules (see below)
├── china-logo.png          # Main header banner image
├── index.html              # Top page
└── README.md               # This document
```

### `news_upload/` File Naming Convention

Files in `news_upload/` follow this format:

```
{year}{semester}_{eventname}[_{order}].ext
```

| Part        | Description                                                                        |
| ----------- | ---------------------------------------------------------------------------------- |
| `year`      | 4-digit year (e.g.,`2025`)                                                         |
| `semester`  | `s` = spring/haru (roughly April–August), `f` = fall/aki (roughly September–March) |
| `eventname` | Lowercase English event name (e.g.,`sungeki`, `kakyo`, `gyoza`)                    |
| `order`     | Integer starting from`1`; **omit `_1` if there is only one file in the group**     |

Special case: kakyo files use `_schedule` and `_result` instead of a number.

Examples: `2025f_sungeki_2.jpg`, `2024s_campustour.pdf`, `2023f_kakyo_schedule.pdf`

## Password Protection

The `member/` directory is protected by HTTP Digest authentication, configured in `.htaccess` per the CNS guide:
https://www.sfc.itc.keio.ac.jp/ja/network_web_virtual2.html (section: "1. パスワードによる制限 (Digest 認証)")

This directory holds content that should not be visible to non-enrolled students (e.g., copyrighted materials). If new restricted content is needed, upload it to `member/`. The username and password are not stored here — ask a current member.

## Security Configuration

The following rules are set in `.htaccess`:

- Requests for git management files, unremovable legacy files, old-site backups, and `README.md` redirect to the top page.
- Requests for nonexistent pages or files redirect to the top page.

## Embedding Videos

Do not upload video files directly to the CNS server — it increases server load. Use an external service instead:

- **Dropbox**: See https://blanche-toile.com/web/website-dropbox for embedding instructions.
- **YouTube**: Use the embed code from the video's share menu.

A long-term goal is to set up a dedicated shared account (e.g., a lab YouTube or Dropbox account) so that video hosting does not depend on any individual member's personal account.

## Miscellaneous Notes

- Banner images sourced from [unDraw](https://undraw.co/) use a consistent 5:4 (width:height) aspect ratio.

## Known Issues / TODOs

- Some pages ported from the old site contain unnecessary legacy tags and CSS classes. Partially cleaned up, but most remain. Cleanup help is appreciated.
- The homepage slideshow (Bootstrap carousel) can behave unstably. A proper fix would require replacing it with a dedicated slider plugin.
- Some button designs and color choices do not match the original design mockup.

## Contact

- 蒋 理嘉 (Faculty of Environment and Information Studies, 4th year) — rika.shou@keio.jp
- 林 琪渊 (Faculty of Environment and Information Studies, 3rd year) — lqywin@keio.jp
- 楊 陶陶 (Faculty of Environment and Information Studies, 2nd year) — quovadis0907@keio.jp
