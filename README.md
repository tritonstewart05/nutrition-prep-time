# Do Healthier Recipes Take Longer? An Analysis of Fitness-Oriented Nutrition and Preparation Time

## Introduction

A common belief is that eating healthy meals, especially high-protein dishes, takes more time than cooking regular meals. Because of this perception, many people avoid meal prepping since they believe it is too time-consuming or inconvenient.

This project investigates whether that belief is actually supported by data.

Specifically, we explore whether meals that are higher in protein and more nutrition-focused take longer to prepare than other types of meals. This question matters because time is one of the most frequently cited barriers to eating healthier or maintaining a fitness-oriented diet. If healthier meals do not take substantially longer to prepare, this challenges the idea that meal prepping is too time-intensive and suggests that eating well may be more accessible than people think.

The first dataset, `recipe`, contains **83,782 rows**, representing 83,782 unique recipes, with several columns describing recipe information.

| Column | Description |
|--------|-------------|
| `name` | Recipe name |
| `id` | Recipe ID |
| `minutes` | Minutes required to prepare the recipe |
| `contributor_id` | User ID who submitted the recipe |
| `submitted` | Date the recipe was submitted |
| `tags` | Food.com tags describing the recipe (e.g., dinner, dessert, low-fat, easy) |
| `nutrition` | Nutrition information in the format [calories (#), total fat (PDV), sugar (PDV), sodium (PDV), protein (PDV), saturated fat (PDV), carbohydrates (PDV)] |
| `n_steps` | Number of preparation steps |
| `steps` | Text describing the recipe steps |
| `description` | User-provided description |
| `ingredients` | Text describing the ingredients |
| `n_ingredients` | Number of ingredients in the recipe |

The second dataset, `interactions`, contains **731,927 rows**, where each row represents a user interaction with a recipe.

| Column | Description |
|--------|-------------|
| `user_id` | User ID |
| `recipe_id` | Recipe ID |
| `date` | Date of the interaction |
| `rating` | Rating given by the user |
| `review` | Text review written by the user |

To answer our research question, we focus on the following relevant columns:

| Column | Description |
|--------|-------------|
| `minutes` | Total time required to prepare the recipe |
| `nutrition` | Nutrition information in the form [calories (#), total fat (PDV), sugar (PDV), sodium (PDV), protein (PDV), saturated fat (PDV), carbohydrates (PDV)]; PDV stands for “percentage of daily value” |
| `n_steps` | Number of preparation steps required |

Given the datasets, we investigate whether recipes that align more closely with fitness-oriented nutrition differ in preparation time compared to less nutritious recipes. To facilitate this analysis, we first separated the values stored in the `nutrition` column into their corresponding columns, including `calories (#)`, `total fat (PDV)`, `sugar (PDV)`, `protein (PDV)`, and others. PDV, or percent daily value, represents how much a nutrient in a serving of food contributes to the recommended daily intake.

Using these nutritional variables, we constructed a measure of recipe “fitness” based on the difference between protein and fat daily value percentages (`protein_pdv - total_fat_pdv`). Recipes with relatively higher protein content and lower fat content were categorized as **High Fitness**, while the remaining recipes were categorized as **Low Fitness**. This grouping allows us to compare preparation times between recipes that are more aligned with fitness-oriented nutrition and those that are not.

The most relevant columns for answering our question include `minutes`, which records the total preparation time of each recipe, `protein_pdv` and `fat_pdv`, which represent the nutritional composition of the recipe, and `n_steps` and `n_ingredients`, which capture the structural complexity of the recipe.

By examining these features, we aim to understand whether healthier recipes tend to require more or less preparation time. Insights from this analysis may help recipe contributors better understand whether creating fitness-oriented meals requires additional preparation effort and whether perceived time constraints are a meaningful barrier to healthier eating.


