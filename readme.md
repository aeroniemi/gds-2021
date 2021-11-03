# Geographic Data Science
- My content from the third year TB1 GDS module
- It probably includes ``r markdown`` files, and regular ``markdown`` files
- It's based on the content at https://www.ljwolf.org/teaching/gds/

## Generics
- The syllabus is at https://www.ljwolf.org/teaching/gds/ and looks really pretty
- It actually looks like its organised
- Split into tidying, visualising and regressing
- Do the reading, show up to the lecture and then wake up insanely early to do the practical the next day
- Practicals are either content or questions - might be worth only including the questions here?
- Maybe turn content into a reference sheet?
- Midterms
- Style is Edward Tufty - maybe I can do that too just in darkmode?
- It's not a programming course *sad*, but I'm gonna go make it look pretty anyway *because there aren't any programming courses to do*
- They really like using mathematical notation - maybe i need to include the maths stuff from learn here

## General terms/functions
### group_by
- Cut data into portions using a column

### summarize
- Take the group and compress it
- With group_by, could be used to get average temperature by year from a per-month dataset

### filter
- Choose rows using a condition

### select
- Choose columns using a condition

### mutate
- Add a column (to the end)

### arrange
- Sort by a column

# Tidy Data
## What is a "tidy data"?
- *Data that is neatly in a box, and not spread out all over the floor - the antithesis of* ***the basement***
- *So this is why it's called* ***tidyverse***
- Effectively:
    - Each table is a **dataset**
    - Each column (*feature*) is a variable: *a type of measurement*
    - Each row is a sample: *one observation*
    - Each cell is a value
- In my lua terms, this means: * *data not accurate*
```lua
aircraftVariant = {
    {
        name = "787-8",
        length = 123,
        mtow = 124502
    },
    {
        name = "787-9",
        length = 456,
        mtow = 144502
    },
    {
        name = "787-10",
        length = 123,
        mtow = 194502
    }
}
```
## How do we actually transform stuff in R?
- Pivot - restructure one table into another using a variable

### Gather
- ``{a, b, c, d, e}`` to ``alphabet = {}``
- Also known as pivot longer
#### ``pivot_longer``
```r
pivot_longer(
    data,
    cols,
    names_to = "name", # what you want the new column for all the old columns called
    values_to = "value", # what you want the values column to be called
)
```
### Spread
-  ``alphabet = {}`` to ``{a, b, c, d, e}``
- Also known as pivot wider

#### ``pivot_wider``
```r
pivot_wider(
    data,
    cols,
    names_from = "name", # the column you want to split based on
    values_from = "value", # the current values column
)
```

#### Need a bar chart to show a axis in a dataset?
```
geom_bar(mapping = aes(x = cut, y = freq), stat = "identity")
```