# Track-Calendly-with-Google-Tag-Manager-and-Google-Analytics-4
Track Calendly with Google Tag Manager and Google Analytics 4

Calendly Tracking process looks like this:

* Create a Custom HTML tag with the listener code. Fire the tag on pages where the Calendly calendar is embedded
* Create a Data Layer Variable and a Custom Event trigger
* Create a Google Analytics 4 event tag that sends the data to Google Analytics
* Don’t forget to test everything with the GA4 DebugView

Listener code::
To start tracking Calendly with Google Tag Manager, you must create a Custom HTML tag in your GTM container. Go to Tags > New > Custom HTML and paste the following code:

cHTML - calendly listener
<script>
window.dataLayer = window.dataLayer ||[];
window.addEventListener('message',
  function(e) {
    if (e.data.event && e.data.event.indexOf('calendly') === 0) {
      window.dataLayer.push({
        'event' : 'calendly',
        'calendly_event' : e.data.event.split('.')[1]
      });
    }
  }
);
</script>

![image](https://user-images.githubusercontent.com/5832613/221227144-281ff77d-7fb6-4426-b2ed-c19f7a55f07f.png)

![image](https://user-images.githubusercontent.com/5832613/221227331-aeda653b-7608-4a40-9c4b-d10526ef16c1.png)

![image](https://user-images.githubusercontent.com/5832613/221227379-abb0d10f-8a42-46b4-a6e3-62ff02a0d9a6.png)


![image](https://user-images.githubusercontent.com/5832613/221226905-06982723-b82c-4fce-beec-171fa9078e78.png)


![image](https://user-images.githubusercontent.com/5832613/221227450-b5f18c8a-0f5e-4e48-b08a-2039e3a68b61.png)

![image](https://user-images.githubusercontent.com/5832613/221228359-debe3070-1bc4-41e1-aac3-a143974e9244.png)


Source:
https://www.analyticsmania.com/post/how-to-track-calendly-with-google-tag-manager-and-google-analytics-4/
https://intigress.com/blog/tracking/calendly-tracking
