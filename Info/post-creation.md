# Post Creation

This document records the current design for creating and publishing Posts.

## Content type selection

When the user selects Create, the first menu allows them to choose:
- Image
- Text
- Carousel

Only Image is currently implemented. Text/Verse and Carousel creation are planned for later.

## Image Post editor

The initial Image Post editor contains a square Image upload area at the top. Selecting it lets the user upload an image, which is then displayed in the editor.

Below the image:

### Title

Title is required.

The Create button is unavailable while any required field is empty.

### Subtitle

Subtitle is optional.

When provided, the Subtitle is used as the short text shown in the Post viewer instead of a Description preview. Opening the description reveals the full Description.

### Description

Description is optional.

If no Subtitle is provided, the viewer can use a short Description preview, such as the first sentence. Opening the description reveals the full Description.

### Age Rating

The Post editor provides an age rating with three choices:
- None: unrestricted
- 16+: restricted to users age 16 and older
- 18+: restricted to users age 18 and older

This is an audience restriction only. Content that is prohibited by the platform remains prohibited regardless of the selected age rating.

There is no separate Post visibility setting. Posts are visible rather than individually marked Public, Unlisted, or Private.

## Advanced Settings

Advanced Settings is collapsed by default.

### Image Settings

Image Settings contains Comic Strip Mode.

If an uploaded image is taller than approximately a 1:2 aspect ratio, the editor can recommend enabling Comic Strip Mode.

When enabled, Comic Strip Mode:
- Treats the image as a vertically scrollable comic strip.
- Aligns the image's left and right edges with the sides of the screen.
- Makes the viewer begin by scrolling through the comic before reaching the Post information/action section.

When disabled, the normal Post viewer is used. The user can tap the image to open a more immersive full-screen image view with support for zooming and similar image-viewing interactions.

## Publishing

After the user completes the editor and presses Create, the platform immediately attempts to publish the Post.

There is no normal draft/pending-publish stage in the successful flow.

If publication fails:
- The user receives a notification about the failure.
- A failed-Post entry appears in the creator's Posts section.
- The failed entry is private and visible only to its creator.
- The creator can open it to inspect the preserved information.
- The creator can choose Recreate to retry publication.
- The creator can correct or replace information before retrying if some information was corrupted or incomplete.

A successful retry publishes the Post normally.
