# Troubleshooting Guide - Image and Resume Issues

## Quick Fixes to Try First

### 1. **Hard Refresh Your Browser**
- **Chrome/Firefox/Edge**: Press `Ctrl+F5` (Windows/Linux) or `Cmd+Shift+R` (Mac)
- **Safari**: Press `Cmd+Option+R`
- This bypasses the browser cache and loads fresh files

### 2. **Clear Browser Cache**
- Go to your browser settings and clear cache/cookies for your site
- Or use incognito/private browsing mode

### 3. **Check Developer Tools**
- Press `F12` to open developer tools
- Go to the **Console** tab - look for any red error messages
- Go to the **Network** tab, refresh the page, and check if `running_pic.png` loads (should show 200 status)

## Test Pages

### Debug Page Test
Visit: `http://localhost:8080/debug.html`

This page will:
- Show if the image loads with JavaScript alerts
- Test both basic and styled images
- Test the resume download
- Display a green border at the top if images load successfully
- Display a red border if images fail to load

### Simple Test Page
Visit: `http://localhost:8080/test.html`

This page has basic tests without framework interference.

## What Should Work Now

### ✅ Resume Download
- All resume links now have `download="Charles_Hough_Resume.pdf"` attribute
- All resume links have `type="application/pdf"` for proper MIME type
- Should force download instead of opening in browser

### ✅ Running Picture Display
- Image appears in **top left of header** on ALL pages
- 80px circular image with navy border
- Responsive (70px on mobile)
- Should be visible on: Home, About, Projects, Journal, Contact

## Common Issues & Solutions

### Issue 1: "Image shows broken/missing"
**Cause**: File path or permissions issue
**Solution**: 
- Check that `assets/running_pic.png` exists (722KB file)
- Verify the file isn't corrupted

### Issue 2: "Image space exists but no image"
**Cause**: Browser cache or CSS conflict
**Solution**:
- Hard refresh browser (Ctrl+F5)
- Try incognito/private mode
- Check browser developer tools for errors

### Issue 3: "Resume opens in browser instead of downloading"
**Cause**: Browser settings or server configuration
**Solution**:
- The download attribute should force download
- Try right-click → "Save link as..."
- Check if your browser has download blocking enabled

### Issue 4: "Changes not showing up"
**Cause**: Browser cache
**Solution**:
- Hard refresh (Ctrl+F5)
- Clear browser cache
- Use incognito mode
- Check if you're viewing the right URL

## File Verification

Your files should contain:

### index.html (line 13):
```html
<img src="assets/running_pic.png" alt="Charles Hough" class="header-profile-pic" />
```

### style.css (around line 33):
```css
.header-profile-pic {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid #002147;
  box-shadow: 0 2px 8px rgba(0, 33, 71, 0.2);
  flex-shrink: 0;
  display: block;
  max-width: none;
}
```

## Still Not Working?

If none of the above works:

1. **Check your hosting setup** - Are you using GitHub Pages, local server, or another hosting?
2. **Try a different browser** - Test in Chrome, Firefox, Safari, Edge
3. **Check the exact URL** - Make sure you're viewing the right page
4. **Verify file paths** - Ensure `assets/running_pic.png` exists and is accessible

## Contact Information
If you're still having issues, please provide:
- Which browser you're using
- Any error messages from developer tools
- Whether the debug page works
- Your hosting setup (local server, GitHub Pages, etc.)