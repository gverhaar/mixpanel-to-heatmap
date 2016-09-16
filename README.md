# mixpanel-to-heatmap
Heatmap on Google Maps showing activity. Using Mixpanel Events as a source (via JQL query). 

**shows number of active users:** It counts a specific event ("User logged in") and displays the count. (You need to change this event name in the index.html if you are using a different event). 

**shows activity as a heatmap:** It reads events. Events with GPS properties will be displayed on Google Maps as a Heatmap, showing where in the world activity is going on. The script uses two properties that are stored with the event:
```javascript
               lon = event.properties.Longitude;
               lat = event.properties.Latitude;
               
```


##Adjust the index.html:

#### 1. change the Event name you want to count as 'active user'

line 70:

```javascript
      var queryParams = {
              fromDate: getDateStr(dateSelect.MPDatepicker('value').from),
              toDate: getDateStr(dateSelect.MPDatepicker('value').to),
              event_selectors: [{event: "User logged in"}]
          }; 
```
Replace "User logged in" with the event name that you store and want to count.
 
#### 2. add your Google Maps Key to the script js/keys.js:
```javascript
var GOOGLE_MAPS_KEY = YOUR_KEY_HERE;
```

### 3. add your Mixpanel API Secret to the script js/keys.js:
```javascript
var MIXPANEL_API_SECRET_KEY = YOUR_KEY_HERE;
```
**Note:** I added the keys to a keys.js to keep them out of GitHub. But you will be able to see the keys through the browser. So at production use a different way to connect to mixpanel.

##And run index.html
Let me know if you find improvements to this sample.

######References:
- started with "A boilerplate data visualization for 3 JQL Queries" https://github.com/mixpanel-platform/mixpanel-jql-webinar-973937-KJWfS0c
- Mixpanel JQL API Reference https://mixpanel.com/help/reference/jql/api-reference
- Heatmaps | Google Maps JavaScript API | Google Developers https://developers.google.com/maps/documentation/javascript/examples/layer-heatmap
