# Newsletter Modal with Crisp Chat Integration

A responsive popup modal that collects visitor emails and integrates with Crisp Chat API to automatically open a chat session with a pre-written introduction message.

## Features

- ✅ **Email Collection**: Validates email addresses with proper error handling
- ✅ **Consent Checkbox**: GDPR-compliant consent mechanism
- ✅ **Crisp Chat Integration**: Sets user email and opens chat widget
- ✅ **Auto Message**: Sends pre-written "About Me" introduction
- ✅ **Multiple Triggers**: Time-based, scroll-based, and manual triggers
- ✅ **Responsive Design**: Modern UI with Tailwind CSS
- ✅ **Accessibility**: Keyboard navigation and ARIA labels
- ✅ **React & Vanilla JS**: Both React component and standalone versions

## React Version (Integrated in Portfolio)

The modal is already integrated into your portfolio (`index.html`) with the following features:

### Triggers

- **Time-based**: Opens after 30 seconds on page
- **Scroll-based**: Opens when user scrolls 50% down the page
- **Manual**: "Let's Chat" button in navigation

### Integration Points

- Crisp Chat script loaded in `<head>`
- Modal component in React islands section
- Modal container in HTML
- Global trigger function exposed

## Standalone Version

For non-React websites, use `newsletter-modal-standalone.html`:

```html
<!-- Include Crisp Chat script -->
<script type="text/javascript">
  window.$crisp = [];
  window.CRISP_WEBSITE_ID = "your-website-id";
  (function () {
    d = document;
    s = d.createElement("script");
    s.src = "https://client.crisp.chat/l.js";
    s.async = 1;
    d.getElementsByTagName("head")[0].appendChild(s);
  })();
</script>

<!-- Include modal HTML and JavaScript -->
```

## Configuration

### Customize About Me Message

```javascript
// In React version, modify the aboutMeMessage prop
aboutMeMessage = "Your custom introduction message here";

// In standalone version, modify the aboutMeMessage property
this.aboutMeMessage = "Your custom introduction message here";
```

### Adjust Triggers

```javascript
// Time-based trigger (React)
setTimeout(() => {
  openModal();
}, 30000); // 30 seconds

// Scroll-based trigger (React)
if (scrollPercentage >= 50) {
  // 50% scroll depth
  openModal();
}
```

### Backend Integration

Uncomment and modify the backend call in both versions:

```javascript
// Optional: Save email to backend/newsletter API
await fetch("/api/subscribe", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ email }),
});
```

## Props (React Version)

```typescript
interface NewsletterModalProps {
  open: boolean; // Controls modal visibility
  onClose: () => void; // Called when modal closes
  aboutMeMessage?: string; // Custom introduction message
  onSubscribed?: (email: string) => void; // Called after successful subscription
}
```

## Styling

The modal uses Tailwind CSS classes and can be customized by modifying:

- **Colors**: Blue theme (`bg-blue-600`, `text-blue-600`)
- **Spacing**: Padding and margins (`p-6`, `mb-4`)
- **Shadows**: Modern shadow effects (`shadow-2xl`)
- **Border Radius**: Rounded corners (`rounded-2xl`)

## Accessibility Features

- **Keyboard Navigation**: ESC key closes modal
- **Focus Management**: Auto-focus on email input
- **ARIA Labels**: Proper form labels and descriptions
- **Screen Reader Support**: Semantic HTML structure

## Browser Compatibility

- ✅ Chrome 60+
- ✅ Firefox 55+
- ✅ Safari 12+
- ✅ Edge 79+

## Testing

1. **Manual Trigger**: Click "Let's Chat" button
2. **Time Trigger**: Wait 30 seconds on page
3. **Scroll Trigger**: Scroll 50% down the page
4. **Form Validation**: Test invalid emails and missing consent
5. **Crisp Integration**: Verify chat opens with pre-written message

## Troubleshooting

### Modal Not Opening

- Check if Crisp script is loaded: `console.log(window.$crisp)`
- Verify modal container exists: `document.getElementById('newsletter-modal-container')`
- Check for JavaScript errors in console

### Crisp Chat Not Working

- Verify website ID is correct
- Check if Crisp script loaded successfully
- Ensure `window.$crisp` is available before using

### Styling Issues

- Ensure Tailwind CSS is loaded
- Check for CSS conflicts
- Verify responsive classes are working

## Customization Examples

### Different Color Scheme

```css
/* Replace blue with green theme */
.bg-blue-600
  →
  .bg-green-600
  .text-blue-600
  →
  .text-green-600
  .ring-blue-500
  →
  .ring-green-500;
```

### Different Trigger Timing

```javascript
// Open after 1 minute instead of 30 seconds
setTimeout(() => {
  openModal();
}, 60000);
```

### Custom Success Message

```javascript
// Modify success state text
<h3 className="text-xl font-bold text-gray-900 mb-2">
  Custom Success Message!
</h3>
```

## License

This code is provided as-is for your portfolio project. Feel free to modify and use as needed.
