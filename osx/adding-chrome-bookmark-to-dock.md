# Adding a Chrome bookmark to the dock

1. Run **Automator**.

2. Create an application:
![screen shot 2017-03-02 at 14 39 09](https://cloud.githubusercontent.com/assets/6684554/23509439/13548188-ff56-11e6-8fe6-0b252fbbdf48.png)

3. Choose the "Run shell script" action (double click it):
![screen shot 2017-03-02 at 14 40 14](https://cloud.githubusercontent.com/assets/6684554/23509469/370c1212-ff56-11e6-89f1-4453c7e24ca4.png)

4. Set the content to `/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --app=` + the URL
![screen shot 2017-03-02 at 14 41 40](https://cloud.githubusercontent.com/assets/6684554/23509517/622863d8-ff56-11e6-97f7-cba90080caa9.png)

5. Hit ⌘+S and save the application in the Applications folder with a chosen name.

## Changing the application icon
1. Right-click the application icon (in the Applications folder).
2. Choose "Get Info".
3. Copy the image of your choice to the clipboard (you can look up a mobile icon in the source code of the page).
4. Click the icon in the top-left corner of the Info window.
5. Press ⌘+V to paste the new icon.
