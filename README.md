# Tails-up Cat Rescue

Tails-Up Cat Rescue is a site for a cat rescue/rehoming centre. The site is aimed at people who are interested in adopting a cat, and showcases a number of cats who need a home. It provides some key information about the personality, attributes and needs of each cat to enable potential adopters to work out whether they might be a suitable 'match'. It also features a form to put those interested in adopting in touch with the centre, and some further information for those new to cat ownership.

## Features 

The site features:

- A 'sticky' navigation bar at the top of the site to enable easy access to each section of the site. The title of the site is also displayed prominently in the navigation bar.
- An 'About' section, which provides some brief background information on the rescue centre and three taglines to explain why Tails-Up Cat Rescue would be a good choice for those looking to adopt a cat. Each tagline is illustrated with a cute cat picture to appeal to potential cat owners.
- A 'Cats looking for a home' section, which features a number of cats currently up for adoption. The name of each cat is provided with a heading, followed by an appealing photo of the cat, a table providing basic details about the cat and a description written in the first 'person'.
- A 'Register' section, which provides the user with a form to complete to register their interest in adopting a cat. The form has required text/email fields requesting basic personal information (first name, last name and email address) and some radio buttons enabling the user to express some basic preferences about the sort of cat they are looking for and the home environment. The form also contains an optional field allowing the user to enter the names of any cats currently up for adoption if they are specifically interested in these.
- A 'Further information' section featuring an embedded Cat Society video providing some basic information for potential cat adopters.
- A footer with links to social media.

In this section, you should go over the different parts of your project, and describe each in a sentence or so. You will need to explain what value each of the features provides for the user, focusing on who this website is for, what it is that they want to achieve and how your project is the best way to help them achieve these things.

The features of the site were 'mocked up' using in a basic wireframe prior to implementation:

![Tails-Up wireframe](read-me_media/tails_up_wireframe_small.png)




### Features Left to Implement


## Testing 

- The use of a sticky header combined with a 'long' page divided into sections meant that while the navigation links to each section functioned correctly, the heading for each section was obscured underneath the header. This was ultimately fixed using the CSS `scroll-margin-top:` property. The first attempt to fix this used `scroll-margin:` on `<section>` elements within the site, however testing the deployed site on a real iPhone exposed a bug causing this property not to work for iOS devices. A Google search found that `scroll-margin-top:` has now been implemented correctly in iOS (source: [https://github.com/mdn/browser-compat-data/issues/7564](https://github.com/mdn/browser-compat-data/issues/7564) ), so this was used instead.
- Testing of the media queries for the responsive design revealed potential issues with content spilling across the hero image for very narrow screen sizes (below about 315px width).
- It was discovered that a value of `fixed` for the CSS `background-attachment:` property is not supported on iOS by testing a deployed version of the site on a real device (the Chrome developer tools do not emulate this behaviour). A value of `scroll` was used in the media queries for small and medium sized devices, to ensure compatibility. This means that only users with a large screen will benefit from a fixed position 'hero' image.
- The page was tested with the VoiceOver screen reader in Mac OS X. This revealed that when navigating through 'landmarks' within the page, only the header, navigation elements, about section and footer were recognised as landmarks. The sections containing the main content of the site were not. Aria-labels were added to each section to rectify this.
- The registration form allows the user to make multiple selections for the age range of cats they are interested in, using checkboxes. The form data is posted to the Code Institute form dump, as this provides useful feedback on the data posted. Testing revealed that multiple selections for the age range checkboxes were not being displayed on the Code Institute response page - only the first value submitted is shown. However, inspecting the data posted by the form in Chrome developer tools demonstrates that the data is being sent correctly, so responding to multiple checkbox values does not appear to be implemented in the form dump. The following screenshot of the Chrome developer tools output demonstrates two values have been successfully submitted for the age-range checkboxes.
![Goole dev tool form data](read-me_media/form_data_screenshot.png)

### Validator Testing 

- The W3C CSS Validator revealed the use of a `text-align` property with a value of `bottom` on the CSS for the `<div>` with an id of `#about-text-container`. As `bottom` is not an allowed value for this property, this line of CSS was having no effect and was removed.

### Unfixed Bugs

## Deployment

## Credits 

### Content 

- Placeholder content used during development generated using [Cat Ipsum Generator](https://fungenerators.com/lorem-ipsum/cat/) (not used in final version)

### Media

Images used in the completed website are:
- The large grey cat 'hero' image used in the About section: [Photo by Pixabay from Pexels](https://www.pexels.com/photo/gray-cat-33537/)

The images used on the wire frame mock-up of the page and as placeholders during development are:
- [Photo by cottonbro from Pexels](https://www.pexels.com/photo/black-cat-on-green-chair-6853506/
)
-   [Photo by Marko Blazevic from Pexels](https://www.pexels.com/photo/cute-gray-kitten-standing-on-a-wooden-flooring-774731/)

The 'Getting Your First Cat' YouTube video in the 'Further Information' section was embedded with permission of the Cats Protection charity:
- [Getting Your First Cat - Cats Protection](https://www.youtube.com/watch?v=sWZTz8KAjfY)



