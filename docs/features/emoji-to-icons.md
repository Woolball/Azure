# Emoji to Icons Conversion

Azure includes an optional feature to automatically convert emojis in your content to Bootstrap icons. This provides a consistent visual style and better accessibility. See this example:

![Emoji to Icons Example](https://github.com/user-attachments/assets/0c77d5e3-aeb2-4079-8f22-a28afad44cef)



## Setup Instructions

1. **Add Bootstrap Icons**

   Add the Bootstrap Icons library to your site by adding this line to your Ghost site's header code injection (Settings > Code injection > Site Header):

   ```html
   <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap-icons/1.11.3/font/bootstrap-icons.min.css">
   ```

2. **Add the Conversion Script**

   Add the following script to your Ghost site's footer code injection (Settings > Code injection > Site Footer):

   ```javascript
   <script>
     document.addEventListener("DOMContentLoaded", function () {
       function replaceEmojisWithIcons() {
         // Select elements with either class
         const elements = document.querySelectorAll(".gh-about-secondary, .gh-content");
         elements.forEach(function(element) {
           // Hide temporarily to avoid flicker
           element.style.visibility = "hidden";
           let content = element.innerHTML;
           
           // Replace emojis with Bootstrap icons
           content = content
             .replace("🔍", '<i class="bi bi-search"></i>')
             .replace("🛠️", '<i class="bi bi-tools"></i>')
             .replace("🚀", '<i class="bi bi-rocket"></i>')
             .replace("✨", '<i class="bi bi-stars"></i>')
             .replace("🧭", '<i class="bi bi-compass"></i>')
             .replace("👥", '<i class="bi bi-people"></i>')
             .replace("👇", '<i class="bi bi-hand-index-thumb" style="display: inline-block; transform: rotate(180deg);"></i>');
           
           // Update HTML and reveal element
           element.innerHTML = content;
           element.style.visibility = "visible";
         });
       }
       
       // Run the function as early as possible
       replaceEmojisWithIcons();
       
       // Set up a MutationObserver for each element (for dynamic updates)
       const targets = document.querySelectorAll(".gh-about-secondary, .gh-content");
       targets.forEach(function(target) {
         const observer = new MutationObserver(replaceEmojisWithIcons);
         observer.observe(target, { childList: true, subtree: true });
       });
     });
   </script>
   ```

## Customizing Icons

You can customize which emojis are replaced and which Bootstrap icons are used by modifying the replacement pairs in the script.

### Default Emoji Mappings

| Emoji | Bootstrap Icon Class     | Description    |
|-------|--------------------------|----------------|
| 🔍    | `bi-search`              | Search         |
| 🛠️    | `bi-tools`               | Tools          |
| 🚀    | `bi-rocket`              | Rocket         |
| ✨    | `bi-stars`               | Stars          |
| 🧭    | `bi-compass`             | Compass        |
| 👥    | `bi-people`              | People         |
| 👇    | `bi-hand-index-thumb`    | Pointing hand  |

### Adding Custom Mappings

To add your own emoji-to-icon mappings, add more `.replace()` lines to the script:

```javascript
content = content
  // Existing replacements...
  .replace("📱", '<i class="bi bi-phone"></i>')
  .replace("💡", '<i class="bi bi-lightbulb"></i>')
  .replace("📊", '<i class="bi bi-graph-up"></i>');
```

### Target Different Elements

By default, the script targets elements with the classes `.gh-about-secondary` and `.gh-content`. You can modify this to target different elements:

```javascript
const elements = document.querySelectorAll(".your-custom-class, .another-class");
```

## Browser Compatibility

This feature works in all modern browsers. The MutationObserver API used for dynamic updates is supported in all major browsers released after 2012.

## Performance Considerations

The script is optimized for performance by:
- Running once at document load
- Using MutationObserver for efficient DOM change detection
- Temporarily hiding elements during replacement to avoid visual flicker

If you notice any performance issues on your site, you can simplify the script by removing the MutationObserver code if your content doesn't change dynamically after page load.
