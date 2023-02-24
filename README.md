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



![image](https://user-images.githubusercontent.com/5832613/221226905-06982723-b82c-4fce-beec-171fa9078e78.png)
