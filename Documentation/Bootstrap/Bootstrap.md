[Back](../Documentation.md)
# Bootstrap

Every Bootstrap class has to be used inside a *.container* (for a fixed width container) or *.container-fluid* (for a full width container).

## Grid System
There are *rows* and *columns* every row works on a 12 column grid across the element

To size columns use `col-s-v` as a class where `s` is the [screen breakpoint](#screen-breakpoints) and `v` is the number of columns you want the element to have as width.  
- example: `col-md-6` to use 6 of the 12 columns

## Screen Breakpoints
| Atribute          | class part |          |
| ----------------- | ---------- | -------- |
| Extra small       | None       | <576px   |
| Small             | sm         | >=576px  |
| Medium            | md         | >=768px  |
| Large             | lg         | >=992px  |
| Extra large       | xl         | >=1200px |
| Extra extra large | xxl        | >=1400px |

## Margin and Padding

To set *margin* or *padding* use `{property}{sides}-{breakpoint}-{size}` where `property` is either [margin or padding](#mp-atributes), `sides` is optional but its for the [side](#mp-atributes) you want to apply the change,`breakpoint` is for [screen breakpoint](#screen-breakpoints), `size` is the [value](#mp-size)

###### M/P atributes
| Atribute   | class part |
| ---------- | ---------- |
| Margin     | m          |
| Padding    | p          |
| Top        | t          |
| Bottom     | b          |
| Left       | l          |
| Right      | r          |
| Vertical   | y          |
| Horizontal | x          |

###### M/P size
| size | multiplier |
| ---- | ---------- |
| 0    | 0          |
| 1    | .25        |
| 2    | .5         |
| 3    | 1          |
| 4    | 1.5        |
| 5    | 3          |
| auto | auto       |