# Frequently Rejected Suggestions

This is a list of features that are commonly suggested for BEEmod, but are either out of scope, not possible due to limitations of Portal 2 itself, or have major functional problems that make them undesirable to implement. Please do not open issues asking for these things to be added, as they will simply be closed.

Also see [Frequently Asked Questions](https://github.com/BEEmod/.github/blob/master/FAQ.md) for general usage/tech support questions.

## New styles

Styles take a lot of work to create and maintain, so new ones are rarely added. For a new style to even be considered, it should make sense overall, work with Portal 2 test chamber gameplay, and be possible to reasonably implement in the Puzzlemaker.

As an example, Portal 1 is a style that fits this criteria, as most of Portal 2's test elements can reasonably exist there and it has a block-based structure similar to Clean. On the other hand, the Behind the Scenes style has very different gameplay from test chambers, making it hard to adapt the existing items into, and it's difficult to make it look good in the Puzzlemaker. BEE2 formerly included a BTS style, but it was never finished and ultimately removed for these reasons.

Other styles like Old Aperture and Overgrown sit at a point in between these - being good fits gameplay-wise, but currently lacking in visual quality, though we would like to improve how these styles look in the future with [decorations](https://github.com/BEEmod/BEE2.4/issues/414) and [chamber exteriors](https://github.com/BEEmod/BEE2-items/issues/3891). Until then, we will not be adding any further styles that depend on these features.

Even if your your suggested style fits the criteria above, we may still not add it if we don't think it's worth the extra maintenance burden. If the style is a simple variant of an existing one (e.g. Original Clean, which just changes wall textures), there is a greater chance for it to be added.

Custom packages can also include styles, so feel free to implement a new style yourself if we won't do it.

## Common feature requests

### Changing editor behavior / making palettes hold more items

The majority of the Puzzlemaker's behavior and functionality is implemented directly within Portal 2's code, so the ability to mod it is extremely limited. While we can add new items and alter the behavior and appearance of resulting maps, we have very little control over the behavior of the editor itself.

Notably, this means the palette is restricted to showing 32 items maximum, which is why the palette swapping system was created in the first place. We also can't customize the labels on item settings (hence "Button Type", "Start Reversed", etc. on many items), create new UIs, or increase connection limits.

### Merging items

While merging items is often a suitable workaround to fit more items on the palette, it's only possible in certain scenarios. All variants of a merged item must have the same properties, collisions, and "item class" (internal setting that defines overarching item behaviors). We combine items whenever we can, so if they aren't combined already, it probably isn't possible.

### Style mixing / changing of items to different styles

We could potentially do this, but we won't. You need the flexibility of Hammer to properly explain style mixing, and lots of combinations wouldn't make sense or may outright break.

### Custom voice lines / Portal 1 GLaDOS lines / lines from mods

It's not possible to properly pack voice lines into maps; while we can pack the actual sounds easily, we cannot include captions or localized versions, which would cause problems for players with hearing disabilities or who don't speak the same language as the map creator.

The Portal 1 GLaDOS lines aren't in Portal 2 by default, making them effectively the same as custom voice lines. Instead, the Portal 1 GLaDOS voice line set simply includes Portal 2 lines which resemble Portal 1 dialogue or allude to the test chambers being older.

For mod voice lines, in addition to these issues, many mod developers do not want their custom voice lines being used in workshop maps.

### Custom gel types / reimplementing Adhesion Gel

Gel behavior is implemented entirely within Portal 2's code, so it's not possible for workshop maps to alter it in any significant capacity or add new gel types. Some maps pull it off by replacing Reflection Gel, but these hacks require maps to be specifically built with them in mind and have various limitations, making them unsuitable for the Puzzlemaker where items are expected to "just work".

Adhesion Gel never functioned properly in any released version of Portal 2, and was replaced with Reflection Gel in the Peer Review update. This effectively makes it no different from a fully custom gel type. Making it work requires further hacks involving *rotating the entire map*, which cannot be reasonably brought into the Puzzlemaker at all.

Note that there are some mods that have licensed Portal 2's code from Valve and used it to implement Adhesion Gel properly. While this makes the gel usable in those mods, it's not possible to include that modified code in workshop maps for the base game, and the mods themselves cannot include the Puzzlemaker as Valve does not provide its code - thus, they are incompatible with BEEmod.

### Giving Reflection Gel a unique color

Reflection Gel was [originally green](https://valvearchive.com/Publications/Portal%202%20-%20Unsuccesses/reflection_gel.jpg), but Valve dummied this out in the final game, causing it to interchangeably pull from either Conversion or Propulsion Gel's colors depending on context. Our only access to these is through the `portal_paint_color` and `speed_paint_color` console variables, which also affect the original gel types, so changing them isn't viable.

We can separately change the color of the mid-air blobs though, which has been done, making them a darker gray compared to Conversion Gel.

### Colorized buttons that can only be activated by a matching cube

This is possible, but it isn't going to be implemented because:

- It would be somewhat complicated to get working properly and not useful for most puzzles.
- Cube colors can be customized, so a mapper could inadvertently choose two colors that were so close together that they were indistinguishable but didn't work together.
- Some players may have colorblindness, again making the cubes hard to distinguish.

The purpose of the cube colorizer is to make it easier to tell which cubes came from which droppers, if one of them needs to be respawned as part of the puzzle. In this case it's fine if they can't be distinguished, since the player can just keep track of that themselves (as if the cubes were uncolored). It's extremely uncommon for a puzzle to need more than two incompatible cube types (cube and sphere), so we don't really think this is worth pursuing, although there has been some discussion of adding a third unique cube shape (such as a triangle).

### Colorized light strips

This is also possible; however, the refraction shader used by light strips isn't compatible with the property used to color other things (e.g. cubes). The app would need to generate individual textures for each selected color, then those would be applied in-game. For this reason, the feature isn't currently being worked on, but could possibly be added in the future.

### Lights that are toggled by an input

The Source engine has very strict limits on toggleable lights. Only two dynamic lights can affect a single surface (although this may have been raised to three in Portal 2), and only 32 possible combinations of light states can exist across the entire map. This makes toggleable lights infeasible for the Puzzlemaker, where users expect items to "just work" and would not be aware of these restrictions.

Additionally, darkness is not a test element and would likely prove to be more of an annoyance than actually contributing to the puzzle design in any way, and aesthetic uses are mostly out of the scope of BEEmod.

### Cores / relaxation vault entrance / other story elements

These are beyond the scope of BEEmod. Story elements tend to be very specially made for the point in the story where they're used, you need the flexibility of Hammer and numerous custom assets to tell a coherent original story. We're not just going to make random Portal 2 setpieces placeable in maps out of context.

While cores arguably have puzzle use via being plugged into sockets, this purpose can already be filled by regular cubes.
