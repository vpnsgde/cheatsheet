# CSS Mastery Cheat Sheet

## 1. Selectors

-   **Universal**: `* {}`
-   **Type**: `div {}`
-   **Class**: `.classname {}`
-   **ID**: `#idname {}`
-   **Group**: `h1, h2 {}`
-   **Descendant**: `div p {}`
-   **Child**: `div > p {}`
-   **Adjacent sibling**: `h1 + p {}`
-   **General sibling**: `h1 ~ p {}`
-   **Attribute**: `input[type="text"] {}`

## 2. Colors

-   **Name**: `color: red;`
-   **HEX**: `color: #ff0000;`
-   **RGB**: `color: rgb(255, 0, 0);`
-   **RGBA**: `color: rgba(255, 0, 0, 0.5);`
-   **HSL**: `color: hsl(0, 100%, 50%);`

## 3. Box Model

    +-------------------+
    |     Margin        |
    |  +-------------+  |
    |  |   Border    |  |
    |  | +---------+ |  |
    |  | | Padding | |  |
    |  | | Content | |  |
    |  | +---------+ |  |
    |  +-------------+  |
    +-------------------+

-   `margin`: Outside space
-   `border`: Border around element
-   `padding`: Space inside border
-   `content`: Text or image

## 4. Positioning

-   `static`
-   `relative`
-   `absolute`
-   `fixed`
-   `sticky`

## 5. Flexbox

    .container {
      display: flex;
      justify-content: center; /* main axis */
      align-items: center;     /* cross axis */
    }

-   `flex-direction`: row, column
-   `flex-wrap`: wrap, nowrap
-   `justify-content`: flex-start, center, space-between
-   `align-items`: flex-start, center, stretch
-   `align-content`: flex-start, center, stretch

## 6. Grid

    .container {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      grid-gap: 10px;
    }

-   `grid-template-rows`
-   `grid-column`
-   `grid-row`
-   `gap`

## 7. Transitions

    button {
      transition: background-color 0.3s ease;
    }

## 8. Transforms

-   `transform: translate(x, y);`
-   `transform: rotate(45deg);`
-   `transform: scale(1.2);`

## 9. Animations

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    div {
      animation: fadeIn 1s ease-in-out;
    }

## 10. Media Queries

    @media (max-width: 600px) {
      body {
        background: lightblue;
      }
    }

## 11. Variables

    :root {
      --main-color: #333;
    }
    div {
      color: var(--main-color);
    }

## 12. Common Units

-   px, em, rem, %, vw, vh
