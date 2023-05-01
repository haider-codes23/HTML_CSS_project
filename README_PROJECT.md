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

## Badge Component

- We have a variation of components like large and small badges, have different colors like light blue and some medium blue, so this where we are going to apply Object Oriented CSS principles. **So the second principle of Object oriented CSS say that we should separate structure from skin.** So we are going to define two classes, one for basic structure in terms of padding and font size and then define few other classes to give badge element a different skin.
- So define a new section in style sheet called badges. First we are going to define a structure, so we’ll start by creating rule for a class called .badge. we are going so set the border-radius to 20px, again we are using pixels because we dont want the radius dependent on the font-size. For padding we are going to use 0.5 rem for vertical and 2 rem for horizontal padding. we’ll set the font-weight to bold. We’ll set white space to nowrap this prevents a badge from wrapping into a second line, this is important when we have limited space e.g. we have a small card and limited space for our badge and we don’t want this badge to wrap in new line, whatever we put inside this badge should always appear in a single line.
- Lets define a skin, so we are going to use a class by the name of .badge—primary, here we are using the BEM (Block Element Modifier) naming convention, so using two hyphens we separate a block or a component from a modifier like primary. In this rule we are going to set the background color to the CSS variable —color-primary and text color to white. Then we are going to define another skin for the secondary color and set background color to —color-secondary and text color to white.
- In your markup create a span element with two classes .badge and  .badge—primary. And for the label we would say 10% off. Our font is a bit to bold so we’ll import Inter 600 as well by appending it in the link in the head element. Right now our badge class is inheriting font-size from the body element which is 2.4 rem or 24 px, but in our design the font-size is 20px, so we will define a new skin in which we will use smaller font size of 15px or 1.5rem and in the badge class we will set the font-size property to 2rem.
- Now create a separate skin for smaller badges with font-size of 1.5rem.
- Now we are done for mobile version now we need to adjust font size for larger screens. So we’ll write a media query for width greater than 1024 px. for the structure we’ll set the font-size to 1.5rem and for skin with smaller font-size we are going to use 1.2rem.

## List Component

- We have a few types of list, horizontal or inline list and vertical list with green ticks. One thing common among these list is that they dont have the default bullet points, the same applies to the navbar and the footer.
- create a section for list in the style sheet
- We’ll create a new class called .list and set the property list-style to none, now we wont have the default bullet points. Also we want to get rid of the left padding that all browser apply by default. Another thing that is common among our list is the color of the text, so our list is not inheriting the main body text color, it’s using the same color as our headings. So we’ll set the color to css variable heading e.g. color: var(—color-headings)\
- Applying the second principle of object oriented CSS lets separate the structure from the skin and create new skin that allows the list to be inline. So we’ll create a class called .list—inline . We want to convert each list item into a inline item, so we’ll go to our markup and give each list element a class of “list__item” and we are going to target items with a class of list__item e.g. .list—inline .list__item and in this class we’ll set the display to inline-block. The list items are too close together so we are going to set the margin right to 2 rem.
- In our design the list have bold items, we shouldn’t go to our list class and set the font size to bold because we have some list that are not bold, so we can do is define a new skin for bold.
- Lets work on list that are vertical and has the green tick before it. Create a class called .list—tick, set the list-type-image property to url() and we’ll pass url() the absolute path of the tick.svg file. Because we has set the left padding to 0 we cant see our ticks so lets apply some left padding. The item are too close to the ticks so we are going to define a new rule for list with ticks with this particular skin, our items should have a left padding. For mobile version there is space between each item in the list so we are going to set the bottom margin of 1 rem. And this we will apply to list items of list with ticks. e.g. .list—tick .list__item { }
- on desktop the space between the vertical list item is smaller so we will write a media query and set the margin bottom to 0.5 rem

## Button Component

- Create a section for button is the style sheet.
- We a various variations of buttons in terms of size and color. Some use accent color and some dont have a background color we only have an outline, we call these buttons outline buttons. This outline button fills it’s container. So in terms of size we have two types of buttons, some button stretch to fill there content and some stretch to take all the available space, we call this button block button. Then we have a outline button with a hover effect, in the call to action section we have another button with secondary color.
- firstly we need to work on the structure of the button for this we define a class called .btn and set font-size to 1.8rem, then the font-weight to 600, then use text-transform property and set it to uppercase, then the words seems to be closer to the borders so add some horizontal padding of 2 rem and vertical padding of 3 rem. Then to get rid of the ugly border we’ll set the border property to 0. To make edges round we’ll use border-radius property and set it to 40px. Then we need to give our button some margin so we’ll give it top and bottom margin of 1 rem and right and left margin of 0 rem. To make the cursor change into a hand pointer we’ll set the cursor property to pointer. And we want to make sure that if we have limited space our button text doesn’t wrap on to a second line. So we are going to use the white-space property and set it to nowrap.
- Next we need to define a few skins for our button, e.g. with background color —color-primary, —color-secondary, —color-accent.
- For each of these skins we are going to apply a hover effect so right after the corresponding skins we apply the hover effect
- Next skin we need to define is for block buttons. So we’ll create a new class called btn-block and set the width property to 100% so that these buttons stretch the entire width of the container. Then we set the display to inline-block. Now if we were using anchor instead of button our text wouldn’t be aligned in the center and button is wider than the screen a and it’s because we haven’t set box sizing so the horizontal padding we have set is added on top of 100% that is why this anchor button is wider than the screen the reason it doesn’t happen to the button element is because by default browsers set box sizing of button elements to border box set the   , so we are going to use the text align property in our .btn class and then we’d go on the top of our style sheet and define a rule using universal selector, so we are going to grab all elements, as well as all elements that are dynamically inserted after or before them for these we are going to set box-sizing to border box. Here we are done with the mobile version lets take care of the desktop version.
- create a media query and set the font-size of .btn class to 1.5rem.

## Input component

- We have an input component that contains a button but not every input component is supposed to have a button. So firstly we are going to implement a basic input component once its ready we’ll combine it with a button.
- create a input element and give a class input. Go the style sheet and define rules for class .input. Set the padding first e.g give it top and bottom padding of 1.5rem and right and left padding of 3.5 rem. Then set the border property to 1rem solid #ccc. And set the border radius to 30px. Then we want to get rid of the dark blue border so we will set the outline property to 0. Then we’ll set the font color to —color-heading and set the font-size to 2rem.
- Our placeholder’s font is a little darker so we will use a pseudo class selector e.g. ::placeholder { } and se the color property to #ccc which is light grey.
- Then we need to decrease the font size for screens wider than 1024 px so we’ll write a media query and write a new rule for input class and set the font size to 1.5rem.

## Input groups Component

- We have a simple input component ready but now how are we going to put the button inside the input component.
- what you see in the design is not the input component, it is giving the illusion of being an input component. In reality we have a div or a container and inside this div we have two elements, an input component and a button, the input component doesn’t have any borders, the actual border is applied to the div or the container.
- So we’ll create a div with a class of input-group. And create an input element with the class input that we created earlier and a button with classes “btn” and “btn—accent”
- In our input-group class we can group an input component or an input field with something else. Here we are grouping it with a button, but we can group it with an icon or any other element.
- inside the input-group class we are going to set the border to 1px solid var(—color-border) and border radius to var(—border-radius). We get a weird layout, first we need to remove the border from the input component, this is where we need to use nesting so if we are in an input-group and that input has an input then that input should not have a border e.g. .input-group .input { border:0 }
- next issue is the placement of the button and that input group has stretched to take up all the available space, because it’s a div which is a block level element. so to push the button to the right we need the input component to grow and take up all the available space. We can use flex here, So we’ll set the display property in class input-group to flex. and
- next we need target the element inside the input-group which has a class of input and we need to set it’s flex-grow property to 1, so that the input component takes up as much space as available and pushes the button to the end of the container.
- Now we need to set the margin around the button. so we define a new rule for buttons within an input-group
- We can also replace the button with an icon. Grab our basic icon tablet from the icons.html and replace it with the button
- when we type something in the input field there is so much space between the icon and input field, so we need to target input components inside the input-group and set the padding to 1.5rem.


## Card Component

- Card have round corners, a header which can be different colors, a body and some shadow around it.
- create a div with a class of “cards”. Create a header element within it a give it class of card__header and for label we’ll add Card Title. Firstly we will built a basic card component, then we’ll add all the other things in it.
- Right next to the header we are going to have a div with a class of card__body and some dummy text inside it.
- Now we need to style this, so we’ll define a rule for class .card. We’ll set the border-radius to 7px and box-shadow to 0(for vertical offset) 0(for horizintal offset) 20px(for blurring) 10px(for spreading the shadow) #f3f3f3(shadow color). Now the card has stretched to take all the available horizontal space, because we are using divs and divs are block level element. we shouldn’t apply width to this component because this component should be fluid and flexible, so we can put it inside any container and the size will be determined by the container. So to make the web site responsive we are going to let the card stretch and take all the available space.
- Next we need to work on the header, for it we’ll define a new rule called card__header and apply a padding of 2 rem(Top and bottom) and 3 rem (right and left). we also wan to apply the same padding in the body of the card, so our elements will be line up properly. so we use a comma and type a second selector e.g. .card__header, .card__body { }.
- Now we need to create two skins primary and secondary with those classes. so with our cards class we’ll add another class called card—primary, then define a rule for it in the style sheet. If we have an element with class card—primary, the header in this element should have a background color of —color-primary and the text white e.g .card--primary .card__header {
  background-color: var(--color-primary);
  color: white;
}


## Plans (This is where we group a card component, with a heading, a badge component , a styled vertical list component and a button)

- So we are going to start of by wrapping our card component in a div with a class plan. So plan consists of a card. The card consists of a footer and a body. The header consists of a bunch of elements e.g. the name of the plan, the price, the billing cycle and a badge and a description.
- So in our header tag we are going to add a bunch of elements. Firstly we use a h3 heading that represents the name of the plan. The reason why we choose a h3 heading is because we have a h2 heading right above it in the design mock up and we dont want to skip any headings because then our mark up wouldn’t be semantic. There should be a proper hierarchy. Then we are going to give our h3 heading a class plan__name, so this is the name element inside the plan container or block and this element plan__name shouldn’t exist outside of this block.
- Next we are going to add a span element for applying styles to our text for the price and give it a class plan__price. The add another span element and give it a class plan__billing-cycle. Then add another span element for the badge  which have the classes badge, badge—secondary and badge—small. And then add another span element for description.
- Now our plan looks way off so lets style it. We’ll start off by defining a rule for class plan__name and set the font color to #fff(white), then set the margin to 0, then decrease the font wight a bit and set it to 500, so thats a little thinner. Then we need to decrease the font size a bit e.g 2.4 rems.
- Next we define a rule for plan__price class. And set the font-size to 6 rem as per our design mock up.
- Next we define a rule for class plan__billing-cycle. And set the font-size to 2.4 rem that’s 24 pixels. Now the text looks a little softer than others so we’ll set the opacity to 0.9. Then our plan__billing-cycle is to close to the badge so we will give it a margin right of 1rem.
- Next we need to define a rule for class plan__description. And set the font-size to 2rem, then set the font-weight to 300 becz our text should look thinner, then letter-spacing to 1px because the space between characters is less. Now if we increase the width of the screen the plan__description moves up along the badge which shouldn’t happen so we set it’s display property to block.
- Now our list items are too close, so we’ll write a new rule for elements with class plan that contain element with class list__items e.g. .plan .list__item { margin-bottom: 2rem;}
- Next we need to write a media query for wider screens, we need to make the the plan__name font-size smaller e.g. from 2.4 to 1.4 rem, the plan__price font-size smaller e.g. from 6 to 5 rem and the plan__description font-size smaller e.g. from 2 to 1.7 rem.