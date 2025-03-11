# Contact Modal Feature

Azure includes an optional contact modal that can display your contact information when users click on your primary CTA button.

![Contact Modal Screenshot](https://github.com/user-attachments/assets/ea90c834-d3fc-4c79-a465-c1733dc2d01b)


## Setup Instructions

1. **Enable the Contact Modal**

   The theme already includes the modal HTML, but you need to add JavaScript to activate it. Add the following code to your Ghost site's footer code injection (Settings > Code injection > Site Footer):

   ```javascript
   <script>
   document.addEventListener('DOMContentLoaded', function () {
     const modal = document.getElementById('contactModal');
     const openModalButtons = document.querySelectorAll('.contact-me-btn');
     
     // Early exit if modal or buttons are missing
     if (!modal || !openModalButtons.length) return;
     
     // Attach event listener to each button
     openModalButtons.forEach(btn => {
       btn.addEventListener('click', function(e) {
         e.preventDefault();
         
         // Re-fetch the email link now, to ensure it's in the DOM
         const emailLink = document.getElementById('emailLink');
         if (emailLink) {
           // Customize this with your own email
           const parts = ['your', 'email', 'example.com'];
           const email = `${parts[0]}.${parts[1]}@${parts[2]}`;
           emailLink.href = `mailto:${email}`;
         }
         
         // Now open the modal
         modal.classList.add('active');
       });
     });
     
     // Close modal when clicking on the close button or the overlay
     modal.addEventListener('click', function(e) {
       if (e.target.closest('.modal-close') || e.target === modal) {
         modal.classList.remove('active');
       }
     });
   });
   </script>
   ```

2. **Customize Your Email**

   In the script above, replace the email parts array:

   ```javascript
   const parts = ['your', 'email', 'example.com'];
   ```

   This approach helps reduce email scraping by bots. The parts will be combined as `your.email@example.com`.

3. **Style Customization (Optional)**

   Add CSS customizations to your Ghost site's header code injection (Settings > Code injection > Site Header):

   ```css
   <style>
   .modal-overlay {
     /* Your custom styles here */
     background-color: rgba(0, 0, 0, 0.8); /* Darker overlay */
   }
   
   .modal-content {
     /* Your custom styles here */
     border-radius: 12px; /* Rounded corners */
   }
   </style>
   ```

## Usage

Once configured, clicking on any element with the `.contact-me-btn` class will trigger the modal. By default, this is attached to your primary CTA button.

To attach the modal to additional buttons, add the `contact-me-btn` class to those elements:

```html
<a href="#" class="contact-me-btn">Contact Me</a>
```

## Advanced Customization

### Custom Modal Content

You can modify the modal content by editing the `contact-modal.hbs` partial in the theme. To do this, you'll need to:

1. Download your current theme
2. Edit the `partials/contact-modal.hbs` file
3. Re-upload the theme to Ghost

### Form Integration

To add a contact form instead of a simple email link:

1. Set up a form service like Formspree, FormKeep, or Netlify Forms
2. Replace the modal content in `contact-modal.hbs` with your form HTML
3. Re-upload the theme to Ghost
