# Site Behavior and Account Interaction Specification

This document records the finalized navigation, profile, comments, notifications, search, account, Tonic, Barrel, and responsive behavior decisions.


## 41. Final top navigation and back behavior

The primary top navigation is a compact bar designed for the mobile-first interface. During the UI skeleton phase, icon placeholders use readable text labels such as [FACE], [SEARCH], [BAR], and [SETTINGS] instead of emoji artwork.

On the Home/Bar screen, it contains, from left to right, evenly distributed across the full top bar with subtle vertical separators:
- A small smiley/face icon. It has no special feature and may simply refresh the current page.
- Search, which opens the Search screen.
- Personal Bar, which opens the user's own Personal Bar.
- Settings, represented by a gear icon, which opens the Settings screen.

There is no separate permanent Notifications button in the top navigation.

Notifications are accessed from the user's Personal Bar through the bell on their bar/table.

The Personal Bar can also be reached through the profile picture on the Home/Bar screen.

On pages where a dedicated in-page Back control is useful, the leftmost top-bar control can become Back instead of the Home smiley. Back returns to the previous page/state.

The site's primary interaction model is touch-first:
- Tap
- Touch and hold
- Swipe gestures where already defined

The browser's normal back behavior should remain functional. The site's Back control is an additional, more accessible navigation control for the same general purpose.

## 42. Settings

Settings is a conventional account/platform settings area.

Opening the gear takes the user to a settings menu that contains the user's profile/account information and controls for editing the information and behavior of their account.

Settings can contain controls for:
- Profile information
- Username and nickname
- Profile picture and background
- Privacy/public visibility controls
- Email
- Password
- Notifications
- Blocked users
- Account deletion
- Other platform/account preferences

The exact visual arrangement can follow a familiar settings-menu pattern.

## 43. Personal Bar and profile behavior

The Personal Bar is both the user's profile and their personal collection area.

The user can:
- Scroll upward to view their Shelf and collection objects.
- Scroll downward to view Posts they have created.
- View their Love Potion.
- View their Salt Jar.
- View their Drunk Tonics, Drunk Barrels, and Drunk Posts where applicable.
- Open the notification bell on their own bar/table.

The Shelf is conceptually plural because it can contain multiple collection objects, even though it is collectively called the Shelf.

A profile's bar/table is visible to other users according to the profile's public/private settings, but the owner's private notifications are not exposed.

When another user views a profile, the bell remains visually present. On another user's profile, selecting that bell opens a direct profile chat rather than exposing the profile owner's notifications.

## 44. Post editing

After publication, the creator can edit the Post's editable information.

Current editable fields include:
- Title
- Description

Editing changes the existing Post rather than creating a replacement Post.

The Post retains its original identity.

Editing does not generate a notification to the creator because the creator already initiated the edit.

If an edit would make the Post invalid, the platform displays an error and does not accept the invalid change.

Additional editable fields can be defined when the Verse and Carousel editors are designed.

## 45. Comments

The comment system follows a conventional nested comment/reply model.

Users can:
- Create comments.
- Reply to comments.
- Expand comment threads to see additional replies.

For a reply thread, the interface can show the first reply initially and provide a control to reveal the remaining replies.

Comments support:
- Upvote
- Downvote

Comments can be disabled on an individual Post.

Users can report comments.

Basic profanity/cuss-word filtering is part of the initial moderation layer.

Detailed comment moderation rules remain a future moderation specification.

## 46. Notification categories and behavior

Notifications are divided into three main categories:

### Comments

Comment notifications cover:
- Someone replying to one of the user's comments.
- Comments on things the user owns or created.
- Relevant comment activity on things the user currently has in their Shelf.

If the user removes an item from their Shelf, they stop receiving ordinary comment notifications associated with that saved item, except for replies to comments the user personally made.

### Project

Project notifications cover activity directly related to things the user owns or created, including:
- Hearts/likes
- Salt
- Mix activity
- Drink activity
- Similar project/content activity defined later

Project notifications can also cover activity involving Tonics the user created or manages.

### General

General notifications cover broad platform information, including:
- Someone Stars/follows the user.
- Platform-generated discovery messages such as recommendations or messages encouraging the user to check out Posts.
- Other general announcements or advertising-style notifications.

Notifications should be grouped so repeated activity about the same thing does not become an unusable stream. The exact batching presentation can be refined during UI implementation.

Drinking something can also generate a notification/event associated with that saved item and can be represented in the appropriate notification/activity system.

When a user is invited to participate in a Tonic or other collaborative collection, the invitation is delivered as a notification and the collection is automatically added to the user's Shelf.

## 47. Search behavior

The Search screen retains the previously defined category and filter controls.

Search categories:
- Posts
- Users
- Tonics
- Barrels

Search filters can be customized to include fields such as:
- Titles
- Descriptions
- Other supported searchable metadata

The user can choose among at least these result-ordering modes:

### Popularity

Results are ordered using popularity signals, primarily the amount of appreciation/likes/hearts associated with the result. The exact weighting can be tuned later.

### Clicks

Results are ordered by click count.

### Relevance

Results are ordered according to how closely they match the user's search query and selected filters.

The relevance system should use standard search-relevance techniques rather than requiring a manually maintained ranking.

The exact search algorithm and filter UI remain implementation details.

## 48. Profile information and privacy

During account creation, the user provides:
- Username
- Nickname
- Password
- Date of birth
- Pronouns
- Optional email
- Initial Barrel selection

Pronouns use the choices:
- He/him
- She/her
- They/them

Multiple pronoun choices can be selected.

The profile can also expose selected information publicly.

By default, fields other than username and nickname can be individually configured as public or private.

Username and nickname are always public.

Email is never publicly displayed.

The profile can optionally show:
- Pronouns
- Date of birth
- Star count
- Total Hearts
- Total Salt
- Total clicks on the user's Posts

Country/state profile fields are not part of the current design.

Users can customize:
- Profile picture
- Profile background
- Background blur amount
- Custom drink appearance

The profile background is displayed behind the profile picture and can be blurred by a user-controlled amount.

## 49. Tonic permissions and membership

The three Tonic permission levels are:

### Viewer

Viewer access is used for private Tonics and allows the invited user to view the Tonic and its contents without editing.

### Editor

Editors can:
- Edit the Tonic description.
- Add Posts to the Tonic.

Editors cannot manage membership or permissions.

### Owner

Owners can do everything Editors can do, plus manage membership and permissions.

The original creator remains the ultimate owner and retains the ability to delete the Tonic.

A non-original Owner cannot delete the entire Tonic.

To invite someone, the inviter enters that user's username. The platform sends the invited user a notification.

Invited users automatically receive the relevant Tonic in their Shelf.

The original owner cannot simply leave ownership behind. If the original owner wants to stop being the owner, they must transfer ownership to another user. A Transfer Ownership control is placed next to the Delete control.

After transferring ownership, the former owner can leave the Tonic.

A non-original Owner can leave normally and loses their Owner role.

## 50. Barrels: administration and content

Barrels are special platform-managed collections.

Only the platform owner or people explicitly hired/authorized by the platform owner can create or manage Barrels.

Ordinary users cannot create or rename/retire Barrels.

Users can add Posts to Barrels through the normal Mix system. This means users effectively suggest content by placing it into the Barrel.

Barrels remain public discovery collections.

## 51. Authentication and password rules

The platform uses standard password authentication.

The minimum password length is 8 characters.

No additional complexity requirement is currently specified. An eight-character password is technically valid even if it is weak.

The platform should still encourage users to choose stronger passwords.

Email is optional during initial account creation.

Email becomes necessary for meaningful creation actions such as:
- Creating Posts
- Commenting
- Other meaningful creation/editing actions

Email verification uses a code sent to the provided email address.

Verification emails should clearly warn users not to give the code to anyone other than the website requesting it.

A user can remove an existing email and later add an email again.

Adding/changing an email follows the normal verification-code process.

Password reset requires an email address associated with the account.

If the account has no usable email address, password recovery is not currently available and the account may become unrecoverable.

Password reset uses an emailed verification code.

## 52. Username changes

A user can change their username once every 30 days.

The new username must be globally unique under the platform's case-insensitive uniqueness rules.

When a username changes:
- The new username becomes reserved for the user.
- The old username becomes available for reuse, subject to the normal uniqueness system.

## 53. Account deletion and 30-day recovery

Account deletion is intentionally difficult to trigger.

The deletion flow includes multiple explicit confirmations.

The user first types the special deletion phrase exactly as currently designed: `DELETe`, with the final "e" lowercase.

The user then confirms using their username.

The platform sends an email confirmation code.

After the code is entered, the interface presents further confirmation steps, including:
- A "Are you really sure?" confirmation.
- A "Are you really, really sure?" confirmation.
- A final "Do you want to reconsider?" confirmation.

The final confirmation uses the same yes/no button color treatment as the earlier confirmation steps.

After deletion is confirmed, the account is scheduled for deletion within 30 days.

During that 30-day period, signing back in can reactivate the account.

The reactivation prompt should explain that the account was scheduled for deletion and ask whether the user wants to reactivate it.

After 30 days, the account is permanently deleted and can no longer be reactivated through normal sign-in.

Surviving Posts follow the platform's archive/anonymization rules.

## 54. Moderation and invalid content

Moderation remains intentionally less specified than the rest of the UI.

The initial system should support:
- Reporting Posts and comments.
- Blocking users.
- Basic profanity filtering.
- Removing content that violates platform rules.
- Handling spam and copying.
- Handling impersonation.
- Account/content strikes.
- Temporary or indefinite bans.
- Appeals.

When content is determined to be prohibited or otherwise invalid under platform rules, it can be removed from public view.

The exact automated filters, moderator tools, evidence handling, strike thresholds, ban durations, appeals process, and legal/copyright policy remain TBD.

## 55. Responsive scope

The first version is optimized for mobile.

The interface is still allowed to render on desktop, but there is no separate desktop interaction system planned at this stage.

The same basic interaction model applies:
- Tap/click
- Touch and hold where supported
- Swipe gestures on touch devices

Desktop-specific keyboard shortcuts and mouse-specific controls are not required for the initial implementation.

## 56. Phase-one implementation scope

The first development phase is the visual/UI skeleton.

It should establish the actual page structure and navigation for:
- Home/Bar
- Top navigation
- Personal Bar
- Other profiles
- Shelf and collection objects
- Feed
- Post viewer
- Post information/action section
- Tonics
- Barrels
- Love Potion
- Salt Jar
- Search and search filters
- Settings
- Notifications
- Profile chat
- Comments and replies
- Mix interface
- Drink/Drunk states
- Heart/Salt states
- Star states
- Potion Tree viewer
- Sign Up
- Sign In
- Sign Out
- Email verification
- Account settings
- Blocked-user settings
- Account deletion/recovery states
- Archived/deleted content

The first skeleton may use mock data and placeholder interactions.

The objective is to establish the complete visual structure before implementing the real database, authentication, recommendation engine, moderation backend, or production media storage.

