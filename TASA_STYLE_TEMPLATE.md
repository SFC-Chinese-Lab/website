# SA/TA Profile and Lab Attendance Schedule Templates

This file preserves the reusable HTML/CSS used in `pages/tasa.html` and `pages/study_room.html`. At the beginning of a new semester, copy the code below and replace the semester, names, photos, and profile text as needed.

## Files That Must Be Updated Together

After the lab attendance schedule is finalized, add the same schedule to both of these files:

- `pages/tasa.html`
- `pages/study_room.html`

SA/TA profile cards only need to be updated in `pages/tasa.html`. Store profile photos in `upload/tasa_profile/`. The capitalization of each filename and file extension must exactly match the path used in the HTML.

## While the Schedule Is Being Finalized

Remove the old schedule's `<style>...</style>` and `<div class="table-wrap">...</div>`, keep the heading, and use this placeholder:

```html
<h1>20XX年度春学期 SA/TA研究室駐在表</h1>
<p>調整中</p>
```

For the fall semester, replace `春学期` with `秋学期`.

## SA/TA Profile Card

Copy the card below into the `<div class="row">` in `pages/tasa.html`. For each additional member, duplicate the complete outer `<div class="col-6 ...">...</div>` block.

```html
<div class="col-6 col-lg-3 p-2 p-lg-3">
  <div class="card h-100 border-0 p-2 px-sm-5">
    <div class="ratio ratio-1x1">
      <img
        src="../upload/tasa_profile/photo-file.jpg"
        class="card-img rounded-circle shadow"
        alt="Name"
      />
    </div>

    <h4 class="card-title text-center mt-2">Name</h4>
    <p class="text-center">
      <b>Role and year</b>
      <br />
      First line of the self-introduction
      <br />
      Second line of the self-introduction
    </p>
  </div>
</div>
```

Replace the following placeholders:

- `photo-file.jpg`: the actual photo filename; the photo should be square (1:1).
- Both instances of `Name`: the visible name and the image's alternative text.
- `Role and year`: for example, `SAリーダー 学部4年` or `修士1年`.
- The two self-introduction lines: if only one line is needed, remove the second `<br />` and the text after it.

## Attendance Schedule CSS

After the schedule is finalized, copy this `<style>` block and the complete table in the next section below the attendance schedule heading.

```html
<style>
  .table-wrap {
    width: 100%;
    display: flex;
    justify-content: center;
    margin: 20px 0;
  }

  .schedule {
    border-collapse: collapse;
    table-layout: fixed;
    width: 1200px;
    text-align: center;
  }

  .schedule th,
  .schedule td {
    border: 1px solid #000;
    padding: 6px;
    vertical-align: middle;
  }

  .schedule thead th[colspan] {
    height: 40px;
  }

  .schedule th {
    width: 100px;
  }

  /* Gray cell for a period with no staff on duty */
  .empty {
    background: #d9d9d9;
  }

  /* Arrange multiple people in the same period horizontally */
  .people {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 8px;
  }

  .people figure {
    margin: 0;
    text-align: center;
  }

  .people figcaption {
    font-size: 12px;
    line-height: 1.2;
    margin-top: 4px;
    white-space: nowrap;
  }

  .avatar {
    width: 56px;
    height: 56px;
    border-radius: 50%;
    object-fit: cover;
    object-position: center;
    display: block;
  }

  .name-only {
    display: inline-block;
    font-size: 14px;
  }

  @media (max-width: 1280px) {
    .schedule {
      width: 100%;
    }

    .schedule th {
      width: auto;
    }
  }
</style>
```

## Staff Member Blocks

When a photo is available, place the complete `<figure>...</figure>` block below inside the appropriate cell's `<div class="people">`. Replace the photo filename, `alt` text, and display name. To show multiple people in one cell, add multiple `<figure>` blocks one after another.

```html
<figure>
  <img
    class="avatar"
    src="../upload/tasa_profile/photo-file.jpg"
    alt="Name"
    loading="lazy"
  />
  <figcaption>Display name</figcaption>
</figure>
```

When no photo is available, use this block to display only the person's name:

```html
<span class="name-only">Display name</span>
```

Use a gray cell for a period with no staff on duty:

```html
<td class="empty"></td>
```

## Complete Attendance Schedule

The following Monday-to-Friday, Period 1-to-5 template can be copied directly. Every white cell contains a `.people` container. Paste staff member blocks into the appropriate containers. For a period with no staff on duty, replace the complete white `<td>...</td>` with `<td class="empty"></td>`.

```html
<div class="table-wrap">
  <table class="schedule">
    <thead>
      <tr>
        <th></th>
        <th>月</th>
        <th>火</th>
        <th>水</th>
        <th>木</th>
        <th>金</th>
      </tr>
    </thead>
    <tbody>
      <!-- Period 1: Monday, Tuesday, Wednesday, Thursday, Friday -->
      <tr>
        <td>1限</td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
      </tr>

      <!-- Period 2: Monday, Tuesday, Wednesday, Thursday, Friday -->
      <tr>
        <td>2限</td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
      </tr>

      <!-- Period 3: Monday, Tuesday, Wednesday, Thursday, Friday -->
      <tr>
        <td>3限</td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
      </tr>

      <!-- Period 4: Monday, Tuesday, Wednesday, Thursday, Friday -->
      <tr>
        <td>4限</td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
      </tr>

      <!-- Period 5: Monday, Tuesday, Wednesday, Thursday, Friday -->
      <tr>
        <td>5限</td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
        <td><div class="people"><!-- Staff member blocks --></div></td>
      </tr>
    </tbody>
  </table>
</div>
```

## New-Semester Update Checklist

1. Update the year and `春学期`/`秋学期` label on both pages.
2. Update the member profile cards in `pages/tasa.html`.
3. Add new member photos to `upload/tasa_profile/`, then verify each filename's capitalization and extension.
4. While the attendance schedule is being finalized, display `調整中` on both pages.
5. After the schedule is finalized, copy the CSS and complete table from this file into both pages.
6. Enter exactly the same staff members and times on both pages.
7. Check both pages at desktop and mobile widths in a browser.
