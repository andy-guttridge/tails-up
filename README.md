# Tails-up Cat Rescue

Tails-Up Cat Rescue is a static website for a cat rescue/rehoming centre. The site is aimed at people who are interested in adopting a cat, and showcases a number of cats who need to be re-homed. It provides some key information about the personality, attributes and needs of each cat to enable potential adopters to work out whether they might be a suitable 'match'. It also features a form to put those interested in adopting in touch with the centre, and some further information for those new to cat ownership. The site includes some basic background information about the rescue centre, and links to social media in the footer.

## Features 

The site features:

- A 'sticky' navigation bar at the top of the site to enable easy access to each section of the site. The title of the site is also displayed prominently in the navigation bar.
- An 'About' section, which provides some brief background information on the rescue centre and three taglines to explain why Tails-Up Cat Rescue would be a good choice for those looking to adopt a cat. Each tagline is illustrated with a cute cat picture to appeal to potential cat owners.
- An 'Available Cats' section, which features a number of cats currently up for adoption. The name of each cat is provided with a heading, followed by an appealing photo of the cat, a table providing basic details about the cat and a description written in the first 'person'.
- A 'Register' section, which provides the user with a form to complete to register their interest in adopting a cat. The form has required text/email fields requesting basic personal information (first name, last name and email address) and some radio buttons enabling the user to express some basic preferences about the sort of cat they are looking for and the home environment. The form also contains an optional field allowing the user to enter the names of any cats currently up for adoption if they are specifically interested in these.
- A separate page opening in a new window to confirm successful submission of the registration form.
- A 'Further information' section featuring an embedded Cat Society video providing some basic information for potential cat adopters.
- A footer with links to social media.
- A 404 error page to reassure the user with a page that clearly belongs to the Tails-Up website and provides links to return to the main site.
- A responsive design providing a suitable layout for smaller screensizes, while maximising the visual appeal for larger screen sizes. The site has three 'breakpoints':
    - For small screens less than 768 pixels wide, the navigation links at the top of the site and all of the content are stacked vertically.
    - For medium size screen between 768 - 1199 pixels wide, the navigation links at the top of the site and the content of the 'About' section are displayed side by side, however the details of the cats in the 'Available Cats' section are stacked vertically.
    - For screens with a width of 1200 pixels and above, the 'Available Cats' content is also spread horizonatally rather than stacked vertically. This layout also features a 'fixed' hero image, for additional visual appeal. This is not implemented for small and medium screen sizes, as some mobile browsers do not implement a `fixed` value for the CSS `background-attachment` property.

The features of the site were 'mocked up' using in a basic wireframe of the layout envisioned for larger screens prior to implementation:

![Tails-Up wireframe](read-me_media/tails_up_wireframe_small.png)

The final site adheres closely to this, however soon after implementation commenced, it was decided to replace the three cat images in the 'About' section with a single 'hero' image. This was a purely aesthetic decision made after browsing some of the cat themed images available for use.


### Features Left to Implement


## Testing 

- The use of a sticky header combined with a 'long' page divided into sections meant that while the navigation links to each section functioned correctly, the heading for each section was obscured underneath the header. This was ultimately fixed using the CSS `scroll-margin-top:` property. The first attempt to fix this used `scroll-margin:` on `<section>` elements within the site, however testing the deployed site on a real iPhone exposed a bug causing this property not to work for iOS devices. A Google search found that `scroll-margin-top:` has now been implemented correctly in iOS (source: [https://github.com/mdn/browser-compat-data/issues/7564](https://github.com/mdn/browser-compat-data/issues/7564) ), so this was used instead.
- Testing of the media queries for the responsive design revealed potential issues with content spilling across the hero image for very narrow screen sizes (below about 315px width). This was fixed by slightly increasing the size of the hero image for small screen sizes.
- It was discovered that a value of `fixed` for the CSS `background-attachment:` property is not supported on iOS by testing a deployed version of the site on a real device (the Chrome developer tools do not emulate this behaviour). A value of `scroll` was used in the media queries for small and medium sized devices, to ensure compatibility. This means that only users with a large screen will benefit from a fixed position 'hero' image.
- The page was tested with the VoiceOver screen reader in Mac OS X. This revealed that when navigating through 'landmarks' within the page, only the header, navigation elements, about section and footer were recognised as landmarks by the screen reader. The sections containing the main content of the site were not. Aria-labels were added to each section to rectify this.
- The registration form was initially coded to submit the form to the Code Institute form dump, to test that it was functioning correctly. The form allows the user to make multiple selections for the age range of cats they are interested in, using checkboxes. Testing revealed that multiple selections for the age-range checkboxes were not being displayed on the Code Institute response page - only the first value submitted is shown:

![Form dump image](read-me_media/form-dump-screenshot.png)

 However, inspecting the data posted by the form in Chrome developer tools demonstrates that the data was being sent correctly, so responding to multiple checkbox values does not appear to be implemented in the form dump. The following screenshot of the Chrome developer tools output demonstrates two values have been successfully submitted for the age-range checkboxes.
![Goole dev tool form data](read-me_media/form_data_screenshot.png)

Once the form was verified to be correctly functioning using the form dump, a separate page to indicate successful submission was created, and the form refactored to link to this page using a `get` value for the `method` attribute of the `<form>` element.

- Testing of the links back to the `index.html` in the header of the 404 error page found that the links were incorrectly formed. This took several attempts to correct, ad resulting in a number of GIT commits and pushes to Github, to ensure they would function correctly on the deployed site. 

### Validator Testing 

#### W3C HTML Validator
- The W3C HTML validator report contained a warning of a possible mis-use of an `aria-label` on line 52 of `html.index`. The `aria-label` had been included for a `<div>` element containing 'taglines' for the site in an unordered list, to provide context for assistive technology in the absence of a heading. The `aria-label` was removed from the `<div>` and added to the nested `<ul>` element instead. This resolved the issue.
- The validator detected a mis-spelling of the `<article>` opening tag on line 136 of `index.html`. Manual inspection revealed that the closing tag on line 166 was also mis-spelled, and the issue was corrected.
- A mal-formed URL in the `action` attribute of the `<form>` element on line 180 of `index.html` was detected and corrected.
- The validator report stated that the `frameborder` attribute on the `<iframe>` element on line 253 of `index.html` is obsolete, and should be replaced with CSS. The code for the `<iframe>` - including the `frameborder` attribute - was derived from the embedded player link provided by YouTube. The offending attribute was removed, and `border: 0px` added to the `styles.css` file to achieve the same effect.
- Once these issues had been addressed, the HTML validation passed with no errors.
- The HTML validator did not produce any warnings or errors for `404.html` or `form-submitted.html`.


#### W3C CSS Validator

- The W3C CSS Validator revealed the use of a `text-align` property with a value of `bottom` on the CSS for the `<div>` with an id of `#about-text-container`. As `bottom` is not an allowed value for this property, this line of CSS was having no effect and was removed. The CSS validation passed with no errors once this had been addressed.

### Unfixed Bugs

- During testing, a series of Cross Origin Resource Sharing (CORS) errors relating to the embedded YouTube video were noted in the Chrome developer tools console. In researching this issue, it was noted that the URL of the site embedding the video should be added to the YouTube URL (i.e. `https://www.youtube-nocookie.com/embed/sWZTz8KAjfY?origin=https://andy-guttridge.github.io/tails-up/`), and this was added to the YouTube URL. However, it appears there are currently unresolved issues with the YouTube player causing such CORS errors (source [https://issuetracker.google.com/issues/229013699?pli=1]). Although this issue remains unresolved, the embedded video functioned correctly in testing.

## Deployment

## Credits 

### Content 

- Placeholder content used during development generated using [Cat Ipsum Generator](https://fungenerators.com/lorem-ipsum/cat/) (not used in final version)

### Media

Images used in the completed website are:
- The large grey cat 'hero' image used in the About section: [Photo by Pixabay from Pexels](https://www.pexels.com/photo/gray-cat-33537/)
- The picture of Muffin the cat is: [Photo by belen  capello from Pexels](https://www.pexels.com/photo/close-up-shot-of-a-russian-gray-cat-8810701/)
- The picture of Gizmo the cat is: [Photo by Gökberk Kılınçarslan from Pexels](https://www.pexels.com/photo/a-ginger-cat-on-wood-10832205/)
- The picture of Star the cat is: [Photo by imustbedead from Pexels](https://www.pexels.com/photo/animal-pet-cute-fur-10813423/)

The images used on the wire frame mock-up of the page and as placeholders during development are:
- [Photo by cottonbro from Pexels](https://www.pexels.com/photo/black-cat-on-green-chair-6853506/
)
-   [Photo by Marko Blazevic from Pexels](https://www.pexels.com/photo/cute-gray-kitten-standing-on-a-wooden-flooring-774731/)

The 'Getting Your First Cat' YouTube video in the 'Further Information' section was embedded with permission of the Cats Protection charity:
- [Getting Your First Cat - Cats Protection](https://www.youtube.com/watch?v=sWZTz8KAjfY)



