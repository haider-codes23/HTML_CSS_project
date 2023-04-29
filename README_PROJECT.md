# HTML & CSS Project Notes

## Modular CSS

- The idea is to break down a page into a bunch of reusable components, and then compose those components together to built a complex layout.
- Each component is built in isolation as if it is the only component that exists.
- Firstly built all the components, when all the components are ready, look great on mobile, tablet and desktop screens we’ll compose those components together.

### Components

1. Navigation Bar
    1. menu —> list —> inline
    
2. Banner/ Hero section
    1. heading
    2. text
    3. button —> component to be built in isolation
    4. image
3. Input field with a button inside it
    1. button —> component to be built in isolation
4. Badges
    1. main badge
    2. multiple variations 
5. list of items horizontally —> inline list
6. Card component —> contains different Elements
    1. Text
    2. price
    3. billing cycle
    4. list with style(green ticks)
    5. button —> component to be built in isolation (light version)
7. Icon
    1. with a round light blue and round background
8. links
9. Grid Component which can be used multiple times 
    1. For Banner/ Hero section
    2. For Card component
    3. For control Panel 
    4. others
10. Control panel component
11. Footer —> lists 

## Choosing Color palette

- A color palette includes a primary color, secondary color and an Accent color
- We are going to define our colors using CSS variables in the style sheet e.g. color for the the card component, color of headings, color of body text

```css
:root {
  -color-primary: #2584ff;
  -color-secondary: #00d9ff;
  -color-accent: #ff3400;
	-color-heading: #1b0760;
	-color-body: #918ca4;
}
```

## Typography

- Is all about Fonts and there Sizes
- We are going to take mobile first approach then we’ll readjust our styles for wider screens.
- Every where on the page one font is used other than in the testimonial section.
- The font used is Inter, we’ll get that from google fonts.
    - Large Heading element use Inter Extra Bold
    - For Body text we’ll use Inter Regular
    - For smaller headings we’ll Inter Bold
    - We will also use Inter Semi Bold
- Now we define a rule for our body element. We’ll set the font-family here so that all elements will inherit it. We’ll set the color for the body element to the CSS variable color-body. For our heading we are going to use a different color so we will define a rule for our heading and set the color for h1, h2, h3 to —color-body. Now we need to set the font-sizes. The h1 element is 70px in the design, but we are going to use a relative unit and write a rule for h1 headings. Firstly we set the font-size of the HTML element to 62.5%, that is equal to 10px. And in the rule for the h1 heading we’ll set the font-size to 7rems that is equal to 70px. The same way our font-size for h2 headings is 40px so we’ll write a rule for h2 and heading and set it’s font-size to 4rem which is equal to 40px. For h3 heading we’ll set font-size to 3 rem. We should also set the font size for body text in the rule for the body  Our body text on mobile is 24 px so we would set it to 2.4 rem. We will also use line height for our body text because the lines are to close. Last thing we want to adjust is the margin below heading 3 and the following paragraph, so that where ever we use a heading 3 and a paragraph there is right amount of space between them. In the design it is 20px, so we’ll set the margin-bottom to 2 rem. But after setting it we still have to much space, margin below the heading is 20 px, top margin of paragraph element is 24 px. So here we have the heading-3 margin and paragraph margin collapsing, so the margin below the heading and above the paragraph has collapsed into 24 px, the reason why setting the margin-bottom property for h3 heading is not making any difference because margin above this paragraph is greater than this value, so to solve this problem we will define a rule for paragraphs to have margin of 0 rem. this way we let the heading decide the margin above the paragraph. Now we want to add this margin below all our headings so we’ll go to the our rule for h1, h2, h3 {} and append the rule there instead of in the h3 heading. All of these setting were for mobile version. Lets figure out setting for laptop or desktop computers. The size of h1 heading is 80 px. Now we’ll write media query for screen larger than 1024px

## Links component

- First component we are going to implement is the link component
- Give it a class of “link-arrow” and a label of Learn More
- In the style sheet firstly define a new section called links so this way we can logically separate various rules. Then define a rule for link-arrow class and set the color property to the CSS variable —color-accent. Next our links don’t have an underline so we’ll define a new rule for all anchors and use the text-decoration property and set it to none. This way we dont have to repeat the property for links in the navigation bar and the footer as well. Next we need to set the links font size and weight keeping mobile view in mind, so we set the font-size to 2 rem and font-weight to bold.
- Next we need to add an arrow after the link, to implement that we are going to use the after pseudo element selector                                                    e.g. .link-arrow::after {content: “—>”}. Then we need to add some space between the link label (Learn More) and  the arrow, so we use margin-left of 5px, the reason we are using pixel is becasue we always want this space to remain same.
- Next we need to implement the hover effect, when we move our cursor over the link the arrow should move a little to the right. So we define another rule .link-arrow:hover::after { }, here we are targeting the after element that we dynamically stated above but in the hover state. The change happens suddenly so apply transition property and make it smooth so set it to margin 0.5s.
- On desktop version our links are little bit smaller, they are 15 px so once again we have to write a media query for wider screens. One option is to add this font size of 1.5 rem for class link-arrow into our media query above for screens wider than 1024 px and then move it at the end of the style sheet. The problem is that this rule will then be far apart from the main rule we defined for mobile. So it’s better to define media query close to each component


One thing To do is create a separate folder called components and then have a sample of each component in that folder. In side that folder create a file called links.html. Then we are going to copy our link element from our index.html markup and then paste it into this file.