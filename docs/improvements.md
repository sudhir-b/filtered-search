# Immediate next steps

 - We should make another component which encapsulates a single JSON entry/search result
   for better modularity and separation of concern, so that the search component doesn't
   have to contain details of the structure of the JSON data file
 
 - At the moment, the search bar only searches by name
   - It would probably be very useful if we were able to search by other
     properties of the contacts in the data, such as company and country
   - The implementation of this might be via radio buttons next to the 
     search bar which allow the user to specify the field they would like to search 

 - We should check that the input field is secure against malicious input
 
 - We should write unit and end-to-end tests
  
 - We should check that the app works consistently across all browsers
   - Currently it has only tested it on Google Chrome, Safari, and Firefox

 - We should come up with a way to deploy this properly in production
   - We might want to containerise the final web app
   - We might also want some form of CI and/or CD in place


# Future improvements
 - Some characters in the JSON aren't displaying properly in three city strings,
   which should be fixed. These strings are:
   - G�ttingen
   - Osnabr�ck
   - Jonqui�re


 - Although the JSON file is only 25KB in size, which is small, it might be worth
   loading it into a database and serving it via a backend, rather than 
   making the client download the whole file every time
   - Cons:
     - This would take longer to implement
     - The search results may be slower to load than if we were doing it all client-side
   - Pros:
     - This would allow the creation, deletion, and updating of the data
       from the client-side
     - This would also be much more scaleable with bigger data sets

 - We might want some sort of authorisation flow before the web app functionality
   is accessible by an end-user, especially if it's displaying personal infomation 

 - There's plenty of room to make the web app look nicer
   - For example, the 'cards' containing the contact information might look
     better if spaced apart
   - The search bar would also look nicer if it was bigger
   - We could probably make good use of [BootstrapVue](https://bootstrap-vue.js.org/)

 - We should address the security issues raised by running `npm audit`