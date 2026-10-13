# DRAW USER GUIDE

With Draw, you can scribble, circle, or highlight parts of a photo directly in the Epicollect5 mobile app — for example, to mark a specimen, a damaged plant, or a location on a map photo.

{% hint style="info" %}
Draw is currently a **beta** feature and is available on the **mobile app only** (Android and iOS). It does not work in the web browser version of Epicollect5.
{% endhint %}

## Before you start

* You need a **photo question** in your project.
* You need to **add a photo** to that question first — Draw always opens on top of an existing photo.

## How to draw on a photo

{% stepper %}
{% step %}
## Open the entry

Open an entry with a photo question that already has a photo, then tap **Edit** (or add a new entry and add a photo).
{% endstep %}

{% step %}
## Open the photo menu

Tap the photo question label (the question text at the top of the card). A menu opens with the available options for that photo.
{% endstep %}

{% step %}
## Open Draw

Tap **Draw Beta** (shown with a brush icon) at the top of the menu. The drawing screen opens with your photo filling the canvas.
{% endstep %}

{% step %}
## Draw on the photo

Draw on the photo with your finger or stylus.
{% endstep %}

{% step %}
## Use the drawing controls

Use the controls in the bottom bar:

* **Undo** — removes the last line you drew. Tap it repeatedly to step back.
* **Clear** — removes all your lines at once. Your photo is never deleted, only the drawings on top of it.
* **1x** (thickness) — opens the pen settings so you can make the line thicker or thinner (1x to 10x).
* **Coloured dot** — opens the pen settings so you can pick a different pen colour.
{% endstep %}

{% step %}
## Change the pen settings

To change the pen, tap either the thickness label or the colour dot. Pick a colour from the grid and/or slide the thickness slider, then tap **Save** to apply, or **Cancel** to keep your previous pen settings.

The new colour only applies to lines you draw from now on — lines you already drew keep their colour.
{% endstep %}

{% step %}
## Save the drawing

When you are happy with your drawing, tap **Save** (tick) in the top right corner. The annotated photo replaces the photo in your entry.
{% endstep %}
{% endstepper %}

## Discarding a drawing

Tap **Cancel** (X) in the top left corner. If you have drawn anything, the app asks you to confirm with **"Discard drawing?"**:

* **Confirm** — closes Draw and your drawing is lost. The original photo stays as it was.
* **Cancel** — returns you to the drawing screen.

## Tips

* Rotate your device while drawing: your lines stay in the right place on the photo.
* Save is disabled for a moment while a large photo is loading — wait for the photo to appear before saving.
* Draw replaces the photo stored in the entry. If you want to keep the untouched original, take or pick the photo again afterwards.
* You can draw on a photo as many times as you like: each time you open Draw, you start from the photo as it currently is in the entry.

## Troubleshooting

<details>

<summary>I cannot see the Draw option.</summary>

Make sure you are using the mobile app (not a browser), the question is a photo question, and a photo has been added. The option does not appear in the PWA/web version.

</details>

<details>

<summary>Nothing happens when I press Save.</summary>

The photo may still be loading. Wait until the image is fully shown, then tap Save again.

</details>

<details>

<summary>The drawing screen closed by itself.</summary>

This happens if the existing photo could not be loaded. Check the photo is still there in the entry, then try again.

</details>
