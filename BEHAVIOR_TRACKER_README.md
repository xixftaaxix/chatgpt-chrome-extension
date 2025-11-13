# Behavior Tracking Web App

A mobile-friendly single-page web application for school staff to track student behavior events in real-time. This app runs entirely in the browser with no backend required, designed specifically for quick and easy use on iPhone through Safari.

## Features

### Four Tracked Behaviors

1. **Elopement** - Frequency + Duration tracking
   - Count how many times the student elopes
   - Time how long each elopement lasts with start/stop timer
   - Displays both count and total duration

2. **Physical Aggression** - Frequency only
   - Track incidents of hitting, kicking, pushing, etc.

3. **Inappropriate Language** - Frequency only
   - Track profanity, rude remarks, etc.

4. **Off-Task Behavior** - Partial Interval recording
   - Tap to record each interval of off-task behavior

## How to Use

### Starting a Session

1. **Select a Student** - Choose from Taylor, Jordan, or Alex on the home screen
2. **Review Behaviors** - See the overview of behaviors to be tracked
3. **Start Session** - Begin tracking with automatic time display

### During a Session

- **Tap any behavior tile** to increment the count
- **Elopement tile** has a special timer button:
  - Tap "Start Timer" to begin timing an elopement episode
  - Tap "Stop Timer" to end the episode and save the duration
  - The timer shows running time or total accumulated time
- **Live clock** in the header shows current time of day
- **End Session** button stops tracking and shows summary

### After a Session

The summary screen displays:
- Total counts for each behavior
- Total duration for elopement events
- Bar graph showing all behavior counts
- Line graph showing cumulative behaviors over time

## Testing Mode

For development and testing purposes, the app compresses a 6-hour school day into 60 seconds:
- All timestamps are normalized to fit in the 60-second timeline
- Time-series graphs show data points scaled to this compressed timeline
- This allows quick testing without waiting hours for data

## Deployment Options

### Option 1: Local File (iPhone Files App)

1. Download `behavior-tracker.html` to your iPhone
2. Open the file from the Files app
3. Safari will open and display the app
4. Optional: Add to Home Screen for app-like experience
   - Tap the Share button
   - Select "Add to Home Screen"
   - The app will appear as a standalone icon

### Option 2: GitHub Pages

1. Fork or clone this repository
2. Go to repository Settings → Pages
3. Select the branch to deploy
4. GitHub will provide a URL like: `https://username.github.io/repo-name/behavior-tracker.html`
5. Open this URL on your iPhone and add to Home Screen

### Option 3: Netlify

1. Drag and drop `behavior-tracker.html` to [Netlify Drop](https://app.netlify.com/drop)
2. Netlify will provide a URL
3. Open on iPhone and add to Home Screen

### Option 4: Vercel

1. Install Vercel CLI: `npm i -g vercel`
2. In the repository directory, run: `vercel`
3. Follow the prompts
4. Vercel will provide a deployment URL

## Technical Details

### Requirements

- **Client-side only** - No backend or database required
- **Internet connection** - Needed only to load Chart.js from CDN
- **Browser compatibility** - Optimized for Safari on iOS
- **Can run offline** - After initial load (if Chart.js is cached)

### Data Storage

- All data is stored in memory during the session
- No persistence - data is lost when the page is closed
- Future enhancement: LocalStorage for session persistence

### File Structure

The entire application is contained in a single HTML file:
- HTML structure for all screens
- CSS styles with iOS-optimized design
- Vanilla JavaScript (no frameworks)
- Chart.js loaded from CDN for visualizations

### Technologies Used

- **HTML5** - Semantic markup with mobile meta tags
- **CSS3** - Gradient backgrounds, flexbox, grid layout
- **Vanilla JavaScript** - No frameworks or build tools
- **Chart.js 4.4.0** - Data visualization library
- **Chart.js date-fns adapter** - Time-series support

## Browser Compatibility

### Fully Supported
- Safari on iOS 12+
- Safari on macOS
- Chrome on desktop and mobile
- Edge on desktop and mobile

### Features
- Touch-optimized tiles for quick tapping
- Responsive design for various screen sizes
- Prevents text selection during rapid tapping
- Auto-updating time display
- Smooth transitions and animations

## Customization

### Adding More Students

Edit the `state.students` array in the JavaScript section:

```javascript
students: [
    {
        id: 4,
        name: "New Student Name",
        behaviors: [
            { id: "elopement", name: "Elopement", type: "Frequency+Duration" },
            { id: "aggression", name: "Physical Aggression", type: "Frequency" },
            { id: "language", name: "Inappropriate Language", type: "Frequency" },
            { id: "offtask", name: "Off-Task", type: "PartialInterval" }
        ]
    }
]
```

### Changing Colors

Update the gradient colors in the CSS for each behavior tile:

```css
.behavior-tile.elopement {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

### Adjusting Test Duration

Change the compressed timeline duration:

```javascript
dayLengthHours: 6,        // Real school day length
testDurationSeconds: 60    // Compressed test duration
```

## Future Enhancements

Potential features for future versions:
- LocalStorage persistence for sessions
- Export data to CSV format
- Multi-student comparison charts
- Daily session archives
- Offline storage and sync
- Print-friendly summary reports
- Customizable behavior types
- Notes field for incidents

## Troubleshooting

### Charts Not Displaying
- **Cause**: No internet connection or CDN blocked
- **Solution**: The app will display a message. Summary data is still available.

### Timer Not Working
- **Issue**: Clicking tile instead of button
- **Solution**: Tap the "Start Timer" button specifically, not the tile itself

### Session Not Starting
- **Issue**: JavaScript error
- **Solution**: Check browser console for errors. Ensure JavaScript is enabled.

### Time Display Not Updating
- **Issue**: Background timer stopped
- **Solution**: Keep the app in foreground or reload the page

## Privacy & Data

- No data is sent to any server
- No cookies or tracking
- No analytics or telemetry
- All data stays in your browser
- Session data is cleared on page close

## License

This behavior tracking app is provided as-is for educational and school use.

## Support

For issues or questions about this app, please file an issue in the GitHub repository.

## Changelog

### Version 1.0 (Current)
- Initial release
- Four behavior tracking types
- Real-time data collection
- Summary with charts
- Mobile-optimized interface
- Compressed testing mode
- Graceful Chart.js fallback
