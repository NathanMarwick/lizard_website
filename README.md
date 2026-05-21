# Bluetongue Lizard Sales Website

This repository controls the lizard sales website published with GitHub Pages. The website is a simple static page: lizard details are stored in `animals.json`, photos are stored in `photos/`, and `index.html` builds the gallery when someone opens the site.

URL: https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
Current URL: https://nathanmarwick.github.io/lizard_website/

Most updates only need two things:

1. Edit `animals.json`.
2. Add, remove, or rename photos in `photos/`.

After changes are committed and pushed to GitHub, GitHub Pages will update the public website automatically. It can take a minute or two for changes to appear online.

The easiest way to update the site is through the GitHub website. You do not need to use the command line unless you prefer it.

## Important Files

- `animals.json` - the list of lizards for sale and site settings.
- `photos/` - photo folders for each lizard.
- `index.html` - the website code. You normally do not need to edit this.
- `sync-photos.sh` - optional command line helper script that makes Git track photos for the lizards currently listed in `animals.json`.

## Editing `animals.json`

On GitHub:

1. Open this repository on github.com.
2. Click `animals.json`.
3. Click the pencil/edit button.
4. Make the change.
5. Click `Commit changes`.
6. Use a short message such as `Update lizard listings`.
7. Commit directly to the main branch.

The file has this structure:

```json
{
  "config": {
    "watermark": "Great Southern Reptiles",
    "formspreeId": "xaqkqzad"
  },
  "animals": [
    {
      "id": "AY2",
      "morphs": ["White Northern"],
      "hets": [],
      "sex": "Unknown",
      "price": 400,
      "dob": "2026-01-22",
      "notes": "White Northern, 66% het Anery, 66% het Hyper"
    }
  ]
}
```

Each lizard entry can use these fields:

- `id` - unique animal ID. This must match the photo folder name exactly.
- `morphs` - visible morphs, written as a list. Use `[]` if there are none.
- `hets` - het genes, written as a list. Use `[]` if there are none.
- `sex` - use `Male`, `Female`, or `Unknown`.
- `price` - number only, without `$` or commas. Use `400`, not `"$400"`.
- `dob` - date of birth in `YYYY-MM-DD` format.
- `notes` - optional extra text shown on the card and detail view.

Supported morph filter names in the website are:

- `Anery`
- `White Northern`
- `Hyper`
- `Albino`
- `T+`
- `Whitesided`
- `Patchwork`
- `Piedsided`
- `Alabaster`
- `Blackout`
- `Platinum`

## Add A New Lizard

On GitHub:

1. Open `animals.json`.
2. Click the pencil/edit button.
3. Copy an existing lizard entry, including the `{` and `}`.
4. Paste it inside the `animals` list.
5. Change the `id`, `morphs`, `hets`, `sex`, `price`, `dob`, and `notes`.
6. Click `Commit changes`.
7. Add photos for the new lizard using the photo steps below.

The same steps in plain editing terms:

1. Open `animals.json`.
2. Copy an existing lizard entry, including the `{` and `}`.
3. Paste it inside the `animals` list.
4. Change the `id`, `morphs`, `hets`, `sex`, `price`, `dob`, and `notes`.
5. Put photos in a matching folder:

```text
photos/NEW_ID/1.jpg
photos/NEW_ID/2.jpg
photos/NEW_ID/3.jpg
```

`1.jpg` is the main thumbnail shown on the gallery page. More photos appear when someone clicks the lizard.

Example new lizard entry:

```json
{
  "id": "NEW_ID",
  "morphs": ["Anery"],
  "hets": ["Hyper"],
  "sex": "Unknown",
  "price": 500,
  "dob": "2026-02-10",
  "notes": "Anery, possible het Hyper"
}
```

Remember to put a comma between animal entries, but do not put an extra comma after the final animal in the list.

## Remove A Sold Lizard

On GitHub:

1. Open `animals.json`.
2. Click the pencil/edit button.
3. Find the lizard by its `id`.
4. Delete that whole entry, from its opening `{` to its closing `}`.
5. Check the commas around the deleted entry.
6. Click `Commit changes`.

Once the animal is removed from `animals.json`, it will no longer appear on the website.

You do not have to delete its old photo folder for the website to work. If you do want to delete the old photos from GitHub too, open the matching folder under `photos/`, open each photo file, use the delete/trash button, and commit the deletion.

## Update A Lizard

To change a price, sex, notes, genetics, or date of birth, edit that lizard's entry in `animals.json` on GitHub and commit the change.

For example:

```json
"price": 600
```

Use:

```json
"sex": "Female"
```

or:

```json
"sex": "Male"
```

## Update Photos

Photos must be JPG files and must be named with numbers starting at `1.jpg`.

Good:

```text
photos/AY2/1.jpg
photos/AY2/2.jpg
photos/AY2/3.jpg
```

Avoid:

```text
photos/AY2/main.jpg
photos/AY2/AY2.jpg
photos/AY2/1.png
photos/AY2/01.jpg
```

If a lizard has no `1.jpg`, the website will show `No photo yet`.

To add or replace photos on GitHub:

1. Open the `photos` folder.
2. Open the folder for the lizard ID, such as `AY2`.
3. Use `Add file` then `Upload files`.
4. Upload JPG photos named `1.jpg`, `2.jpg`, `3.jpg`, and so on.
5. Click `Commit changes`.

If the folder does not exist yet:

1. On your computer, make a folder named exactly the same as the new animal ID, for example `NEW_ID`.
2. Put the JPG photos inside it as `1.jpg`, `2.jpg`, `3.jpg`, and so on.
3. Open the `photos` folder on GitHub.
4. Use `Add file` then `Upload files`.
5. Drag the whole `NEW_ID` folder into the upload area, or drag the numbered JPG files in if GitHub is already showing the correct animal folder.
6. Click `Commit changes`.

GitHub does not keep empty folders, so the new photo folder only exists once at least one photo has been uploaded into it.

The folder name must match the `id` in `animals.json` exactly. For example, animal `AY2` uses `photos/AY2/1.jpg`.

## Check For Mistakes Before Publishing

When editing on GitHub, watch for any warning or red error marker in the editor before committing.

If the website later says it cannot load animal data, `animals.json` probably has a formatting error.

Common mistakes are:

- missing commas between lizard entries
- an extra comma after the last lizard
- missing quote marks around text
- square brackets missing from `morphs` or `hets`

## Publish Changes To GitHub Pages

When using the GitHub website, clicking `Commit changes` publishes the update to the repository. GitHub Pages will rebuild the site after the commit. Wait a minute or two, then refresh the public website.

If the old version is still showing, refresh the browser. Sometimes it helps to do a hard refresh or open the page in a private/incognito window.

## Optional Command Line Workflow

These steps are only needed if you are working from a computer with Git and a terminal.

After editing, run these commands from the repository folder:

```bash
git status
bash sync-photos.sh
git add animals.json photos README.md
git commit -m "Update lizard listings"
git push
```

Use this routine each time animals are added, removed, sold, or updated from the command line:

```bash
cd /scratch/pawsey0964/tpeirce/lizard_website
python3 -m json.tool animals.json
bash sync-photos.sh
git status
git add animals.json photos README.md
git commit -m "Update lizard listings"
git push
```

## Troubleshooting

If the website says it cannot load animal data, `animals.json` probably has a formatting error. If you are using the command line, run:

```bash
python3 -m json.tool animals.json
```

If you are only using the GitHub website, reopen `animals.json` and check the most recent edit for commas, quote marks, and brackets.

If a lizard appears but has no photo, check:

- the folder is named exactly the same as the lizard `id`
- the first photo is named `1.jpg`
- the photo is inside `photos/LIZARD_ID/`
- the changes have been committed and pushed

If a lizard does not appear, check:

- the lizard entry is inside the `animals` list
- the JSON is valid
- the changes have been pushed to GitHub
- the browser is not showing an old cached version of the page

## Site Settings

The `config` section in `animals.json` controls site-wide settings:

- `watermark` - text drawn over photos.
- `formspreeId` - Formspree form ID used by the visitor gate before showing the gallery.

Only change these if you are intentionally changing the business name or contact form.
