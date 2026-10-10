# SA/TA Profile and Lab Attendance Schedule Templates

This file preserves the reusable HTML/CSS used in `pages/tasa.html` and `pages/study_room.html`. At the beginning of a new semester, replace the semester, attendance availability, names, photos, and profile text as needed. Attendance cells display only `あり` or `なし`; names and photos belong in the profile cards.

## Files That Must Be Updated Together

After the lab attendance schedule is finalized, add the same schedule to both of these files:

- `pages/tasa.html`
- `pages/study_room.html`

SA/TA profile cards only need to be updated in `pages/tasa.html`. Store profile photos in `upload/tasa_profile/`. The capitalization of each filename and file extension must exactly match the path used in the HTML.

## While the Schedule Is Being Finalized

Remove the complete `<div class="attendance-table-wrap">...</div>`, keep the heading, and use this placeholder. The shared table styles remain in `style/main.css`:

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

## Attendance Schedule Styles

Both pages load the shared attendance table styles from `style/main.css`. Use `.attendance-table-wrap` for the wrapper and `.attendance-table` for the table. The table fits the page width on desktop and mobile. Header cells have a light gray background; cells with `なし` use `.attendance-unavailable` and a darker gray background.

## Availability Cells

For a period with at least one staff member on duty, use:

```html
<td>あり</td>
```

For a period with no staff on duty, use:

```html
<td class="attendance-unavailable">なし</td>
```

Confirm each period's availability before publishing. Keep `調整中` on both pages until the schedule is confirmed; `なし` means that no staff member is scheduled, rather than an unconfirmed period.

## Complete Attendance Schedule

The example below is the confirmed 2026 fall schedule, Monday to Friday and Period 1 to 5. For a new semester, replace the availability in every cell with the confirmed schedule, then copy the same table to both pages. Give the schedule heading `id="attendance-heading"` so the table's `aria-labelledby` points to it. Keep `scope="col"` on weekday headers and `scope="row"` on period headers.

```html
<div class="attendance-table-wrap">
  <table class="attendance-table" aria-labelledby="attendance-heading">
    <thead>
      <tr>
        <th scope="col">時限</th>
        <th scope="col">月</th>
        <th scope="col">火</th>
        <th scope="col">水</th>
        <th scope="col">木</th>
        <th scope="col">金</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th scope="row">1限</th>
        <td>あり</td>
        <td class="attendance-unavailable">なし</td>
        <td class="attendance-unavailable">なし</td>
        <td class="attendance-unavailable">なし</td>
        <td>あり</td>
      </tr>
      <tr>
        <th scope="row">2限</th>
        <td>あり</td>
        <td>あり</td>
        <td>あり</td>
        <td class="attendance-unavailable">なし</td>
        <td>あり</td>
      </tr>
      <tr>
        <th scope="row">3限</th>
        <td>あり</td>
        <td class="attendance-unavailable">なし</td>
        <td>あり</td>
        <td class="attendance-unavailable">なし</td>
        <td>あり</td>
      </tr>
      <tr>
        <th scope="row">4限</th>
        <td>あり</td>
        <td>あり</td>
        <td>あり</td>
        <td class="attendance-unavailable">なし</td>
        <td>あり</td>
      </tr>
      <tr>
        <th scope="row">5限</th>
        <td>あり</td>
        <td class="attendance-unavailable">なし</td>
        <td>あり</td>
        <td class="attendance-unavailable">なし</td>
        <td class="attendance-unavailable">なし</td>
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
5. After the schedule is finalized, copy the complete table into both pages, using the shared styles in `style/main.css`.
6. Enter exactly the same `あり`/`なし` values for every weekday and period on both pages.
7. Check both pages at desktop and mobile widths in a browser.
