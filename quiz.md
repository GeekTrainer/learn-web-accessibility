Which of the following is an accessible link?

- `<a href="https://www.microsoft.com">https://www.microsoft.com</a>`
  - Incorrect. The URL should not be used as the link text because a screen reader will read the URL to the user.
- `<a href="https://www.microsoft.com">Microsoft</a>`
  - Correct. Providing a few words to describe where the link will take the user is accessible link text.
- `<a href="https://www.microsoft.com/>Click here</a>`
  - Incorrect. Text like "here" and "click here" is indiscernible to a screen reader.

Which of the following is an appropriate use of ARIA (Accessible Rich Internet Applications) attributes?

- To indicate to a screen reader a `div` element is actually a `button`
  - Incorrect. ARIA attributes are not designed to be used to avoid semantic HTML.
- To provide different text for a screen reader to speak when using link text which reads "click here".
  - Incorrect. ARIA attributes are not designed to be used to avoid creating good link text
- To give context to a screen reader when creating a control which doesn't exist in semantic HTML, such as a tree.
  - Correct. ARIA attributes can provide context to a screen reader when creating custom controls which don't exist natively in HTML.

You need to add a control which the user will click or tap on to perform an action. What HTML element should you use?

- `div`
  - Incorrect. While it is possible to make any control clickable, using a `button` will ensure your page is accessible.
- `span`
  - Incorrect. While it is possible to make any control clickable, using a `button` will ensure your page is accessible.
- `p`
  - Incorrect. While it is possible to make any control clickable, using a `button` will ensure your page is accessible.
- `button`
  - Correct. You should use `button` to ensure your page is accessible.