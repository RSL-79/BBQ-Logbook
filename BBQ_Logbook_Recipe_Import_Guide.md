# BBQ Logbook — ChatGPT Recipe Import Guide

Use this guide when asking ChatGPT to create a recipe import file for BBQ Logbook.

## What to ask ChatGPT
Tell ChatGPT: "Create a BBQ Logbook recipe import JSON file from this recipe. Follow the attached BBQ Logbook Recipe Import Guide exactly."

## Recipe types
- `bbq-log` — a BBQ recipe that should create a full logged cook.
- `bbq-recipe` — a smoker/BBQ recipe that does not need a full cook log.
- `kitchen` — a non-BBQ recipe.

## Core JSON fields
```json
{
  "name": "Recipe name",
  "type": "bbq-log",
  "category": "Main Dish",
  "servings": 6,
  "prepMinutes": 20,
  "cookMinutes": 360,
  "proteins": ["Beef"],
  "cut": "Tri-Tip",
  "ingredients": [
    {"quantity":"2","unit":"lb","item":"tri-tip","section":"MEAT"}
  ],
  "steps": [
    "Season the 2 lb tri-tip.",
    "Preheat smoker to 225°F."
  ],
  "notes": "",
  "pellets": "Ultimate Blend",
  "rubs": [],
  "startTemp": 225,
  "wrapTarget": 165,
  "afterWrapTemp": 225,
  "pullTarget": 200,
  "restMinutes": 60
}
```

## Ingredient rules
Each ingredient should use separate `quantity`, `unit`, and `item` fields. Use `section` when a recipe has groups such as FOR THE MEATBALLS or FOR THE SAUCE. Quantities may use cooking fractions such as `1/4`, `1/2`, `3/4`, and `1 1/2`.

## Direction rules
Directions must repeat the exact ingredient quantity needed in that step whenever the source recipe provides it. For example, write "Add 1/2 cup milk" rather than "Add milk." Do not invent quantities that are missing from the source recipe.

## Protein and Cut / Item
`proteins` contains broad browse tags such as Beef, Pork, Poultry, Seafood, Lamb, Game, or Other. A recipe may use more than one protein, for example `["Beef","Pork"]`.

For `bbq-log` recipes, `cut` is the specific item used for cook planning/history, such as Tri-Tip, Brisket, Pork Shoulder / Pork Butt, St. Louis Ribs, or Ground Meat / Meatballs.

## BBQ-only fields
For BBQ recipes, include pellet/rub and temperature/rest fields only when known from the source. A blank wrap target is valid. Do not invent smoker temperatures, wrap temperatures, pull temperatures, rest times, servings, or other missing recipe facts.

## Important
Output valid JSON only when creating the import file. The user can import the resulting .json file from BBQ Logbook > Recipes > Import Recipe.
