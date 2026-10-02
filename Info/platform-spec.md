# Social Media Thing: Master Platform Specification

This is the current detailed source of truth for the Social Media Thing design. It records decisions from the planning process so the project does not depend on conversational memory. Newer decisions supersede older ideas. Items marked TBD are intentionally undecided.

## 1. Core concept

Social Media Thing is a mobile-first social platform centered on visual discovery, collections, lightweight social actions, and user-created connections.

The main discovery experience can use a Pinterest-like masonry/collage feed, but the platform's distinctive feature is the connection system: users Mix Posts into Tonics or Barrels, and those relationships create navigable Potion Trees.

The project should first receive a complete UI skeleton. The major screens, buttons, shelves, bars, menus, states, and navigation should exist before every feature is functional. Functionality can then be added incrementally.

## 2. Content types

### Posts

A Post is the standard image-based content item.

A Post has:
- Media
- Title
- Description
- Creator attribution

The initial version supports images. GIF uploading is explicitly postponed and is not a current requirement.

The exact maximum file size and supported image formats are implementation decisions to be selected later.

### Post creation and publishing

The current Create flow begins by asking the user to choose a content type:
- Image
- Text
- Carousel

Only Image creation is implemented in the current design. Text/Verse and Carousel creation are planned for later.

For an Image Post, the creation screen contains:
- Image upload area/button at the top. The selected image is displayed in the editor.
- Title, which is required.
- Subtitle, which is optional.
- Description, which is optional.
- Age Rating, with the choices None, 16+, and 18+.
- Advanced Settings, collapsed by default.

There is no Post visibility selector. Posts are visible; users do not choose Public, Unlisted, or Private for individual Posts.

If a required field is empty, the Create button is unavailable. A Post is not submitted until all required fields are filled.

The Age Rating is an additional audience restriction, not permission to post otherwise prohibited material. Inappropriate content remains prohibited regardless of its selected age rating.

After the user submits a valid Post, the platform immediately attempts to publish it.

If publication fails, the platform:
- Shows the user a notification about the failure.
- Places a private failed-Post entry in the creator's Posts section. Other users cannot see this failed entry.
- Preserves the available Post information so the user can inspect it.
- Allows the user to open the failed entry and view its information.
- Provides a Recreate action so the user can retry publication.
- Allows the user to correct or replace information before retrying if something was corrupted or incomplete.

A successful publication creates the Post immediately rather than placing it into a normal draft queue.

### Verses

A Verse is a text-based post.

Eventually, Verses should have a visual editor with:
- Background customization
- Built-in gradients
- Text customization
- Gradient text
- Basic themes
- Custom styling

The advanced Verse editor is a later feature.

### Carousels

A Carousel contains multiple pieces of content, such as multiple images and/or text content.

A Carousel behaves as one content item in browsing. Its exact editing interface is TBD.

## 3. Feed dimensions

The feed is a masonry/collage layout.

Mobile:
- Two columns.

Desktop:
- Four columns.

Feed items use an approximate aspect-ratio range from 2:1 landscape to 1:2 portrait. The original dimensions determine the height within that range. Content outside the allowed range can be cropped in the feed.

These restrictions apply to feed cards only.

After a user opens a Post, the viewer becomes full-screen and shows the actual media. The feed card's aspect-ratio limits no longer apply.


### Image settings and Comic Strip Mode

Advanced Settings contains Image Settings for Image Posts.

Comic Strip Mode is an optional setting for unusually tall images. If an uploaded image is taller than approximately a 1:2 aspect ratio, the editor can recommend enabling Comic Strip Mode.

When Comic Strip Mode is enabled:
- The image is presented as a vertically scrollable comic strip.
- Its left and right edges are aligned with the sides of the screen.
- When the viewer first opens the Post, the user scrolls through the comic strip before reaching the Post information/action section.

When Comic Strip Mode is disabled, the Post uses the normal image presentation. The user can tap the image to open a more immersive full-screen image view, where zooming and other image-viewing interactions can be supported.

These Comic Strip rules affect the Post viewer presentation, not the feed card's aspect-ratio limits.

## 4. Persistent Posts and archival deletion

Posts are persistent content objects. A Post can be associated with an account without being fundamentally dependent on that account's continued existence.

A normal Post can link to its creator's profile, and the creator's profile can link back to the Post.

If a Post is deleted, it becomes an archive representation rather than simply disappearing.

The archive retains:
- The actual media
- The title
- The description
- Anonymous creator attribution

The archive removes normal social information such as:
- Hearts
- Salt
- Comments
- Other interaction information that should not survive deletion

The archive is effectively read-only.

The purpose is long-term continuity. If someone remembers a Post years after discovering it, the Post can still exist even if its creator deleted it.

If an account is deleted, its surviving content can similarly become anonymous archive content.

A future cleanup system may permanently remove content that has not been viewed or meaningfully encountered for an extremely long time. The threshold is TBD and should be conservative.

## 5. Tonics

A Tonic is a user-created collection, similar in broad purpose to a Pinterest board.

Anyone can create Tonics.

Tonics can contain unlimited content.

Normal Tonics can be shared with other users using three permission levels.

### Viewer

Can view the Tonic and its contents.

Cannot edit.

### Editor

Can edit everything about the Tonic and its contents.

Cannot invite, remove, or manage other users.

### Owner

Can do everything an Editor can do and can manage membership and permissions.

The original creator is the ultimate owner. Even another Owner cannot permanently delete the entire Tonic. Only the original creator can delete it.

Private Tonics are not publicly listed and are accessible only to the creator and invited users.

When viewing a Tonic, its primary collection action is Drink. A Tonic does not use Mix as its primary action.

## 6. Barrels

A Barrel is a platform-created public collection.

Ordinary users do not create Barrels. The platform owner creates them.

Barrels can be based on trends, topics, or useful discovery categories.

Barrels:
- Are public
- Can be followed
- Can be Drunk
- Can receive Posts through Mix
- Can contain unlimited content
- Are platform-created
- Serve as discovery starting points

Barrels have a barrel-shaped visual identity, but they do not need to be displayed as giant literal barrels everywhere.

When a user first joins, they can browse the available Barrels and choose approximately three to follow as their initial discovery sources.

When viewing a Barrel, its primary collection action is Drink. A Barrel does not use Mix as its primary action.

## 7. Shelf

A Shelf is the user's collection area.

It can contain:
- Drunk Tonics
- Drunk Barrels
- Drunk Posts
- Love Potion
- Salt Jar
- Other future collection objects

Posts are not added to the Shelf through Drink. Posts can still appear in special collections such as Love Potion and Salt Jar.

## 8. Drink

Drink is an action, not a content type.

Drink means saving or collecting something to the user's Shelf.

Drinking is unlimited and is never intended to be paywalled or consume Salt.

A user can Drink:
- Tonics
- Barrels
- Posts

Posts can be Drunk and are saved in the user's Drunk area.

The visual container differs:
- A Drunk Tonic can use a potion-bottle-like container.
- A Drunk Barrel can retain a barrel-inspired appearance.

After a Tonic or Barrel is Drunk, its Drink button changes to the state Drunk. Selecting Drunk again removes it from the Shelf.

The Drink action can have a visual animation using colors or visual elements inspired by the saved content.

Drink is not a popularity vote or limited currency.

## 9. Heart and Love Potion

Heart is unlimited normal appreciation.

Heart means that the user likes something.

Hearting a Post places it into the user's Love Potion.

The Love Potion is a special heart/potion-shaped Shelf collection containing all Hearted items.

Hearting also influences feed recommendations through connected discovery. A Hearted Post is a strong indication that the user likes that kind of content. Posts that branch from, or are meaningfully connected to, Hearted content can therefore be considered for recommendations. The recommendation system should not simply recommend every connected Post; it should use the connection as one signal among other discovery signals.

Opening the Love Potion uses the normal collection-page structure but has a special blush transition:
- A blush circle in the center
- Two additional blush circles to the left and right, slightly lower
- Blush lines around the effect

The exact animation can be refined later.

## 10. Salt and Salt Jar

Salt is limited special appreciation.

Salt is limited to a daily allowance.

Salt is never purchasable.

Using Salt:
- Adds Salt appreciation to the Post.
- Adds the Post to the user's Salt Jar.
- Influences feed recommendations through connected discovery.

Removing an item from the Salt Jar:
- Does not refund the Salt.
- Does not remove the Salt appreciation from the Post.

Salt also influences feed recommendations through connected discovery. A Salted Post is a stronger indication of the user's interest than an ordinary view. Posts that branch from, or are meaningfully connected to, Salted content can therefore be considered for recommendations. The recommendation system should not simply recommend every connected Post; it should use the connection as one signal among other discovery signals.

The Salt Jar is a personal collection of Salted items.

Its visual is a jar containing cube-like pieces resembling salt or sugar cubes.

Opening the Salt Jar uses a freeze-style visual effect.

## 11. Star

Star is the following system.

A user Stars a creator/channel.

Starred creators can have their Posts appear in the user's feed.

A user's list of Stars is private. Other users do not see who they have Starred.

A creator's profile displays its Star count.

## 12. Mix

Mix creates connections and organizes content.

A Post can be Mixed into:
- A Tonic
- A Barrel

Direct Post-to-Post Mix is not part of the current system.

The basic flow is:
1. Open a Post.
2. Select Mix.
3. Choose a Tonic or Barrel.
4. The Post is added there.
5. The relationship contributes to the Potion Tree.

Mix is similar to putting something into a folder, but the important difference is that these placements create a network of relationships.

Everything inside a Tonic or Barrel is connected for Potion Tree exploration.

Mix does not directly modify feed recommendations. However, Mix relationships can become the connection paths used by Heart and Salt recommendation signals. In other words, a Hearted or Salted Post can cause relevant content branching from that Post through the connection network to become eligible for recommendation.

Mix should be quick and low-friction. Users do not manually draw trees.

## 13. Potion Trees

A Potion Tree is a graph-based exploration interface generated from Mix relationships.

It is not a giant global graph of the entire platform.

The Tree can be opened from a Post's Extra Options menu.

The current Post appears as a node or bubble.

From that node, the interface shows the Posts most frequently clicked from that particular Post during exploration.

The target is approximately the top 10 connected Posts per node.

This ranking is based on click-through relationships, not simply total views.

Selecting a connected Post makes it the current node and reveals its own connections.

This can continue indefinitely in depth.

The visual concept resembles an Obsidian-style connected-node graph, with bubbles and lines.

The same Post cannot appear twice in the same explored route. This prevents infinite loops.

If a Post has no connections, the exploration stops providing further choices.

A future version may show the route taken as a small tree/path when the user reaches a dead end.

## 14. Connection tracking

The system distinguishes normal Post views from click-through relationships.

For example, if users repeatedly choose Post B after starting from Post A, the A-to-B relationship becomes stronger for Potion Tree display.

This is intentionally different from simply ranking B by its total number of views.

## 15. Home / Bar

The normal Bar is the homepage and discovery area.

The initial home view contains:
- The user's profile picture
- The bar/table interface
- The beginning of the feed
- Search
- Settings

The user can scroll into the feed.

The profile picture is a navigation control. Selecting it opens the user's Personal Bar.

## 16. Personal Bar

A Personal Bar is the user's profile page.

It contains:
- Profile picture
- Account information
- Shelf
- Special collections
- Created Posts

The Shelf comes before the user's created Posts.

The Shelf can contain Drunk Tonics, Drunk Barrels, Love Potion, and Salt Jar.

The profile distinguishes collected content from content actually created by the user.

## 17. Other user profiles

A creator's profile contains:
- Profile picture on the left
- Username in bold to the right
- Star count near the username
- Stats button
- Bar/table
- Visible shelf contents
- Created Posts farther down

Creators can decide which Shelf material is visible to other people.

Visible shelf content may include Drunk Barrels, Drunk Tonics, Love Potion, Salt Jar, and other supported objects.

The creator's actual Posts are shown separately farther down the page.

## 18. Usernames and nicknames

Usernames are globally unique.

Capitalization does not matter for uniqueness. For example, differently capitalized versions of the same username count as the same username.

Allowed username characters currently include:
- Letters
- Numbers
- Minus/hyphen
- Plus
- Equals
- Underscore
- Period
- Caret/to-the-power-of symbol

Parentheses and exclamation marks are not part of the current username character set.

Nicknames do not need to be unique.

Nicknames can contain anything permitted by moderation.

Profile pictures can be animated.

## 19. Post viewer

Selecting a Post opens a full-screen viewer.

The actual media is shown rather than a constrained feed card.

If the media is unusually long, the user can scroll through it.

At the bottom is the Post action bar.

The Post viewer has a top navigation bar. On the Home/Bar page, its leftmost control is currently a placeholder icon, followed by Search and Settings. On a Post viewer, the leftmost control becomes Back, followed by Search and Settings.

The Post itself occupies essentially the full screen beneath the top bar. The viewer then scrolls into a Post information/action section containing:
- Creator profile picture
- Creator/channel name
- A divider
- Title
- Subtitle, if configured; otherwise a short preview of the Description, such as its first sentence
- A Description area that can be opened to reveal the full Description
- The Post action row
- A divider
- Related/Mixed Posts

The related/mixed section is based on actual Mix relationships surrounding the current Post. It can include Posts that are in the same Tonic or Barrel and other Posts connected through the Mix system. A separate ranking/display system will determine exactly which related Posts are surfaced and in what order.


Current actions, from left to right:
- Mix, represented by a shot-glass-style icon and the primary connection action
- Extra Options, three dots
- Comment, chat bubble
- Heart, heart icon

Mix is deliberately the far-left primary action because creating connections is a defining part of the platform.

The Post action bar uses four visible controls rather than separate buttons for every action.

The shot-glass Mix control supports:
- Tap: Mix the Post into a Tonic or Barrel.
- Touch and hold, then swipe upward: Drink, where the available target is a Tonic, Barrel, or Post.

The Heart control supports:
- Tap: Heart the Post.
- Touch and hold, then swipe upward: Salt the Post.

The exact gesture animation and affordance are UI implementation details, but the four-button interaction model is part of the current design.


Posts do not need a separate visible Drink button. Mix is the Post's primary visible connection action, while Drink is available through the hold-and-swipe interaction.

## 20. Extra Options and Share

Extra Options is a three-dot menu.

The initial menu contains:
- Share
- Potion Tree

Future utilities such as downloading can be added later.

Share is a normal external sharing utility. Its initial purpose is simply to give the user a link they can copy and send through other apps.

Share does not create a Mix relationship.

## 21. Comments

Posts can have comments.

The system is conventional:
- Users can comment.
- Users can reply to comments.
- Comment threads can be viewed.

Comments generate notifications.

Detailed comment moderation is TBD.

## 22. Notifications

Notifications can be generated by:
- Hearts
- Salt
- Drinks
- Mixes
- Comments
- Replies
- Future interaction types

Notifications are grouped first by the thing they are associated with.

For example, activity associated with one Post is grouped under that Post.

Within that item, activity can be organized by action type such as Heart, Salt, Comment, Reply, and similar actions.

Exact batching thresholds and notification timing are TBD.

## 23. Search

Search is available from the main interface.

The Search screen contains:
- Search field
- X button inside the search field to clear it
- Category selector
- Search/filter settings

The category choices are:
- Posts
- Users
- Tonics
- Barrels

Search filters can determine whether the search looks through:
- Titles
- Descriptions
- Other future searchable fields

The exact filter UI is TBD.

## 24. Settings

A gear button opens Settings.

Settings is the general location for account and platform controls.

Potential settings include:
- Account
- Privacy
- Blocked users
- Email verification
- Username changes
- Notifications
- Display preferences
- Other account controls

The exact final settings list is TBD.

## 25. Feed recommendations

Initial feed discovery comes from the user's selected Barrels.

Drink is a major discovery signal:
- Drunk Tonics can expose their contents as discovery sources.
- Drunk Barrels can expose their contents as discovery sources.

Star is also a discovery signal because Posts from starred creators can appear.

Heart is a recommendation signal. Hearted content can lead to recommendations of relevant Posts connected to that content.

Salt is also a recommendation signal. Salted content can lead to recommendations of relevant Posts connected to that content.

Mix itself does not directly act as a preference vote. Its connection relationships can provide the branches through which Heart and Salt recommendation signals discover related content.

The system should not treat a Heart or Salt as a command to recommend every connected Post. Connected content is eligible as a recommendation source, with relevance, connection strength, prior interactions, and other future recommendation signals considered as well.

The exact recommendation algorithm will be designed later.

## 26. Account creation

The platform uses:
- Sign Up
- Sign In
- Sign Out

Login is not the preferred terminology.

A user can create an account without verifying email immediately.

Before email verification, the account is primarily view-only.

Users must verify their email before they can make Posts or perform meaningful creation/editing actions.

Password reset and recovery details are implementation decisions for later.

## 27. Username changes

Users can change their username once every 30 days.

The new username must still satisfy global uniqueness and character rules.

## 28. Private accounts

Users can enable private account mode.

Private mode makes their identity less publicly visible rather than deleting their content.

Anonymous attribution can use the word Anonymous plus the first character of the username.

If the username contains no letters, the first character is still used.

Exact private-account behavior for every object type is TBD.

## 29. Blocking

Users can block other users.

Blocking should remove the blocked user's account and created content from the blocker's experience.

This includes:
- Their profile
- Their Posts
- Tonics they created
- Other content directly created by them

Content that the blocked person merely follows or edits is not automatically treated as their created content.

Blocked users can be found in Settings.

## 30. Moderation

Moderation will be designed separately.

Current concepts include:
- Reports
- Blocking
- Spam/copying enforcement
- Impersonation enforcement
- Inappropriate-content enforcement
- Strikes
- Temporary bans
- Indefinite bans
- Appeals

The previously discussed severity levels are:
- Moderate
- Major
- Severe

The previously discussed strike concept is three strikes leading to a ban, with old strikes eventually stopping their active count while remaining visible in account history.

Previously discussed ban durations were:
- Moderate: one week
- Major: one month
- Severe: indefinite

These details are not yet final.

## 31. Impersonation and copying

Using another creator's theme, name style, profile imagery, edits, or reactions can be acceptable in contexts such as fan content, subject to moderation.

Directly reposting another person's content exactly is not intended to be allowed.

Falsely claiming to actually be another person is not intended to be allowed.

The exact copyright/legal policy is TBD.

## 32. Monetization

The platform is not built around purchasing social influence.

Salt is never purchasable.

Drink is never limited or paywalled.

Cosmetic purchases are not a core system.

Possible future donation/support cosmetics could include a badge on the user's bar table.

A voluntary subscription/support system can be considered.

Creator monetization is postponed.

Advertising should be limited and unobtrusive. Ads may appear alongside ordinary Posts. Exact frequency and placement are TBD.

## 33. Visual direction

The site is mobile-first and also has a desktop presentation.

The general direction is:
- Dark mode
- Minimalistic
- Slightly cartoon-like
- Bar/potion themed
- Not realistic

Some earlier visual constraints such as mandatory sharp corners and thin gray borders are flexible and can be improved during actual UI design.

The important layout requirements are:
- Two feed columns on mobile
- Four feed columns on desktop
- Feed aspect range approximately 2:1 through 1:2
- Full-screen Post viewer after opening content

## 34. Post viewer background

When a Post is opened, the same media can become the page background.

The background:
- Uses the same source media
- Is enlarged proportionally until it covers the page
- Is heavily blurred
- Is not stretched unnaturally
- Mainly provides the colors/atmosphere of the Post

The actual media remains readable in the foreground.

## 35. Navigation map

Important navigation paths include:

Home/Bar -> Post -> Creator Personal Bar

Home/Bar -> Tonic -> Tonic contents

Home/Bar -> Barrel -> Barrel contents

Home/Bar -> Search -> Posts / Users / Tonics / Barrels

Personal Bar -> Shelf -> Drunk Tonic / Drunk Barrel / Love Potion / Salt Jar

Post -> Extra Options -> Share / Potion Tree

Potion Tree -> connected Post -> connected Post -> ...

The final animations and exact transitions are UI implementation details.

## 36. Collection page behavior

Selecting a Barrel opens a collection page showing the Barrel's category/name and its bar/table interface, followed by its contents.

Selecting a Tonic uses the same general layout, replacing the Barrel identity with the Tonic name.

Selecting the Love Potion uses the same general layout and shows liked/Hearted things, with the blush effect.

The Love Potion entrance animation is:
- One blush circle appears at the exact center.
- Two additional blush circles appear to the left and right, slightly lower than the center circle.
- Blush lines appear around the circles.
- After the transition, the normal Love Potion collection view is shown.

The blush effect is purely visual and does not change what Heart means or how Hearted content is stored.

Selecting the Salt Jar uses the same general layout and shows Salted things, with the freeze effect.

Selecting a normal Post has no special collection effect. It opens the full-screen Post viewer.

## 37. Account deletion and surviving content

Deleting an account removes the active account identity.

The platform's archive system means the user's Posts do not need to be destroyed.

Surviving Posts become anonymous/archive content.

The account itself no longer behaves as an active profile.

The user's active Tonics cease to exist as active collections when the account disappears. Their Posts can remain.

Deleting a Tonic removes the Tonic as an active collection, but its Posts are not automatically destroyed.

The platform should preserve useful underlying content relationships where possible instead of leaving unexplained broken references.

## 38. Development plan

The first implementation stage is the full UI skeleton.

The skeleton should contain:
- Home/Bar
- Feed
- Personal Bar
- Other user profiles
- Shelves
- Posts
- Full-screen Post viewer
- Tonics
- Barrels
- Love Potion
- Salt Jar
- Search
- Search filters
- Settings
- Notifications
- Comments
- Extra Options
- Share UI
- Mix UI
- Drink and Drunk states
- Heart state
- Salt state
- Star state
- Potion Tree placeholder/viewer
- Sign Up
- Sign In
- Sign Out
- Email verification state
- Account settings
- Blocked-user settings
- Archive/deleted-content states

The first skeleton does not need every button to function.

After the visual structure is stable, features can be implemented one by one.

## 39. Deferred technical architecture

Database design is intentionally postponed until the product specification is sufficiently complete.

Implementation will eventually need to model:
- Persistent Posts
- Media storage
- Accounts
- Profiles
- Tonics
- Barrels
- Tonic permissions
- Shelves
- Hearts
- Salt
- Salt Jar entries
- Stars
- Mix relationships
- Potion Tree click-through statistics
- Comments and replies
- Notifications
- Search
- Archived Posts
- Account anonymization
- Moderation
- Storage cleanup
- Authentication

The database should reflect the principle that content can survive account deletion.

## 40. Glossary

Bar = homepage/discovery area.

Personal Bar = a user's profile page.

Post = standard image content.

Verse = text-based content.

Carousel = multiple content pieces presented as one item.

Tonic = user-created collection.

Barrel = platform-created public collection and discovery starting point.

Drink = action that saves a Tonic, Barrel, or Post to the Drunk area.

Drunk = saved state produced by Drink.

Heart = unlimited normal appreciation.

Love Potion = Shelf collection of Hearted items.

Salt = limited special appreciation.

Salt Jar = Shelf collection of Salted items.

Star = following a creator.

Mix = placing a Post into a Tonic or Barrel and contributing to the connection network.

Potion Tree = graph exploration generated from Mix relationships.

Shelf = saved/collected content area.

Extra Options = three-dot Post menu.

Archive = preserved read-only representation of deleted content.

Anonymous = attribution used when a creator no longer has an active public identity.


## 41. Final top navigation and back behavior

The primary top navigation is a compact bar designed for the mobile-first interface.

On the Home/Bar screen, it contains, from left to right:
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
