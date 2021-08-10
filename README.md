# Google_Sheet_Appscript


#OAuth workflow steps

**Step 1** . Open a new Google Sheet and open up Script Editor. As per usual, you can clear out the boilerplate myFunction() code.

**Step 2** . Click on Resources > Libraries...:
![img1](https://user-images.githubusercontent.com/80478598/128831028-200b3bdb-ebb7-46f0-9836-da6fe1df04c4.png)

A library is a re-usable body of code to do a specific function, in this case handle the OAuth process, which we can use by linking to the library from within our Apps Script project.

**Step 3** . Add the OAuth2 library project key:

1B7FSrk5Zi6L1rSxxTDgDEUsPzlukDsi4KGuTMorsTQHhGBzBkMun4iDF

and select the most recent version 

![img2](https://user-images.githubusercontent.com/80478598/128831128-bd4d18eb-d3e1-4d01-8531-bee615f84939.png)

**Step 4** . Add a second apps script file, called Oauth.gs, to your project, so you have the following two apps script files in the left pane of your Script Editor:

-->   Code.gs
-->   Oauth.gs

**Step 5** . Add the code of the given Code.gs file into  sheet code.gs file.

**Step 6** . Add the code of the given Oauth.gs file into  sheet Oauth.gs file.

**Step 7** . The redirect URL takes this form:

https://script.google.com/macros/d/{SCRIPT ID}/usercallback

where we need to replace {SCRIPT ID} with our own script ID, which we get from the “File > Project properties”:

![img3](https://user-images.githubusercontent.com/80478598/128831746-f22b80d9-7b74-4baa-8ca8-412c65ee89b8.png)

This is the script id:

![img4](https://user-images.githubusercontent.com/80478598/128831752-fcfbc210-6d68-42ca-8165-bbda316ce62f.png)


Copy this script ID into the redirect URL, replacing {SCRIPT ID} (including the curly braces {}) with your own script ID, and then make a copy of the full URL somewhere (for step 9).

**Step 8** . To get the application’s URL, publish the project as a web application: “Publish > Deploy as web app…”:

![img5](https://user-images.githubusercontent.com/80478598/128832097-2bfa63a1-dc27-455d-96f9-70aedb2e5908.jpg)

Copy the current web app url.

**Step 9** . Time to register our application in GitHub.

Go to the developer GitHub pages, login and create a new application.

![img6](https://user-images.githubusercontent.com/80478598/128832371-4f7ca069-33ad-42d2-88d8-5d56e8221f7d.png)

You’ll be prompted to enter some application details:

![img7](https://user-images.githubusercontent.com/80478598/128832377-08ac4c82-37de-4589-9350-d261c946977d.jpg)

**Step 10** . Enter a project name, the web app url (from step 8) and redirect url (from step 7) into the respective fields, as follows:

![img8](https://user-images.githubusercontent.com/80478598/128832595-5adfa684-a802-4db5-888d-b17fd807811d.png)

**Step 11** . You should then see your app credentials page where you can get your Client ID and Client Secret:

![img9](https://user-images.githubusercontent.com/80478598/128832953-cf5c2d99-1625-47cc-9cc5-7a3ff93ef35b.png)

Copy the Client ID and the Client Secret into the placeholders on lines 1 and 2 of the code in the OAuth.gs file.

**Step 12** . Back in your Script Editor, run the onOpen() and getUserRepos() functions. From the vantage point of your script editor it’ll look like nothing has happened, but the onOpen function will have added the menu to your Sheet, and the getUserRepos will have logged the URL you need to complete the authorization (see the next step, step 14).

**Step 13** . In your script editor, open the logs to get this authorization URL (go to View > Logs, or press Cmd + Enter):

![img10](https://user-images.githubusercontent.com/80478598/128833136-343ac845-a72c-48b0-afb5-d5b92100d344.png)

**Step 14** . Copy this entire url and paste it into your browser, which should redirect to the GitHub authorization page:

![img11](https://user-images.githubusercontent.com/80478598/128833252-e00a8fec-2c9f-4880-b54d-53ecdc4c7a81.png)

**Step 15** . Click “Authorize” and you’ll be prompted to enter your password:
![img12](https://user-images.githubusercontent.com/80478598/128833417-d79a144c-e215-4884-8676-4028d5292ec8.png)

You’ll then be redirected to the success page, meaning your Apps Script successfully connected to GitHub’s API using OAuth:

![img13](https://user-images.githubusercontent.com/80478598/128833431-3d3c5295-bc34-4f71-b413-28d9e302562f.png)

**Step 16** . Now run your getUserRepos() function again and you should see all the repo information returned from the API:

![img14](https://user-images.githubusercontent.com/80478598/128833749-a52bd565-0634-47f4-96af-cb8501009de7.png)

Congratulations!!

You now have a working OAuth2 application that pulls data from the GitHub API into your Google Sheets environment.

**Step 17** . Go forth and build your GitHub/Sheets applications!

