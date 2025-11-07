# Navigation Testing Guide

## How to Test Navigation

### Browser Console Test

1. Open `index.html` in your browser
2. Open Developer Tools (Press `F12`)
3. Click on the **Console** tab
4. You should see output like:

```
🎬 Pitch Deck Script Loaded
Found slides: 7
Slide IDs: slide1, slide2, slide3, slide4, slide5, slide6, slide7
✓ Next button click listener attached
✓ Prev button click listener attached
Audio visualizations created
```

### Manual Navigation Tests

#### Test 1: Click Buttons
- Look for two circular arrow buttons in the bottom-right corner
- Click the right arrow (→) button
- Console should show: `Next slide: 2 of 7`
- Slide 2 should display
- Click the left arrow (←) button
- Console should show: `Prev slide: 1 of 7`
- Slide 1 should display

#### Test 2: Keyboard Arrows
- Open the presentation in browser
- Press the **Right Arrow** key on your keyboard
- Console should show: `Next slide: 2 of 7`
- Slide 2 should display
- Press the **Left Arrow** key
- Console should show: `Prev slide: 1 of 7`
- Slide 1 should display

#### Test 3: Wrap Around
- Go to the last slide (Slide 7)
- Press Right Arrow
- Should wrap to Slide 1 with console showing: `Next slide: 1 of 7`
- Go to Slide 1
- Press Left Arrow
- Should wrap to Slide 7 with console showing: `Prev slide: 7 of 7`

#### Test 4: Progress Bar
- As you navigate, the progress bar at the top should fill proportionally
- Slide 1: Progress bar ~14% full
- Slide 4: Progress bar ~50% full
- Slide 7: Progress bar ~100% full

### Expected Behavior

✅ Button clicks advance/retreat slides  
✅ Arrow keys advance/retreat slides  
✅ Progress bar updates with each slide  
✅ Audio waves animate on each slide  
✅ No console errors (check for red text in console)  
✅ Slides wrap around at the beginning/end  

### If Navigation Doesn't Work

**Check Console (F12 > Console tab):**
1. Do you see `🎬 Pitch Deck Script Loaded`?
   - If NO: JavaScript isn't loading - check HTML file
   - If YES: Continue to step 2

2. Do you see `Found slides: 7`?
   - If NO: Slides aren't being found - check HTML for `.slide` class
   - If YES: Continue to step 3

3. Do you see `✓ Next button click listener attached`?
   - If NO: Buttons aren't found - check HTML for `id="nextBtn"` and `id="prevBtn"`
   - If YES: Buttons are ready

4. When you click buttons, do you see navigation logs?
   - If NO: Click listeners might not be working - try refreshing page
   - If YES: Navigation is working!

5. When you press arrow keys, do you see navigation logs?
   - If NO: Keyboard listener might not be working
   - If YES: Keyboard navigation is working!

### Troubleshooting

**Problem: Buttons not visible**
- Check that bottom-right of page has two circular arrow buttons
- Open CSS in browser DevTools to verify `.slide-navigation` styling
- Ensure buttons have `position: fixed; bottom: 2rem; right: 2rem;`

**Problem: Buttons not clickable**
- Try clicking directly on the arrow symbols
- Ensure no other elements are on top with higher z-index
- Check that `z-index: 100` is applied to `.slide-navigation`

**Problem: Keyboard keys not working**
- Try clicking on the slide area first to give it focus
- Ensure you're pressing the actual arrow keys, not numpad arrows
- Check that you're not in an input field

**Problem: Still not working?**
- Hard refresh browser: Ctrl+Shift+R (or Cmd+Shift+R on Mac)
- Try a different browser (Chrome, Firefox, Safari)
- Check the browser console for JavaScript errors (red text)
- Make sure `js/script.js` is loading (check Network tab in DevTools)

