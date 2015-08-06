# ppm
Private Package Manager

##Pages

###Upload a new package (/upload)
####User interface
- File Upload field accepting apk, zip, tar
- Text field that accepts URLs
- Button that:
    1) if file has been dragged in the browser sends the file through a web form
    2) if link has been typed in the text field, sends the value of the textfield through a web form

- View List button which brings the user to /list page

####How it works
- When user uploads a file the server:
    - creates a new folder in folder uploads with name = current timestamp (using Date.now() for example)
    - saves the file with its original name in the created folder

- When user saves a URL link the server:
    - creates a new folder with name = current timestamp (using Date.now() for example)
    - saves a txt file that contains the link that has been send by the client

###List of packages (/list)
####User interface
- <ul><li> list in a jade template that represents sorted by date packages

- each li contains:
  - QR code area which is empty by default but if user clicks on the <li> the QR code gets generated. QR actually contains the link of the package or the url from the txt file.
  - a text representing the link to the package or the url from the txt file. In both cases the text is auto selected on click so user can ctrl+c the link and send it if they want

- Upload button that brings the user to /upload page


##Examples

###Example data

    uploads
         1438803474679
              project-one.zip

         1438803506571
              project-two.zip

         1438803526958
              url.txt - this file will contain http://staging.lexicum.net/mobile

         1438803600403
              url.txt - this file will contain http://staging.lexicum.net/desktop


###Example list page

    <ul>
        <li>
            <div class="qrcode"></div>
            <span>Wed Aug 05 2015 22:40:00 GMT+0300 (EEST) http://staging.lexicum.net/desktop </span>
        </li>
        <li>
            <div class="qrcode"></div>
            <span>Wed Aug 05 2015 22:38:46 GMT+0300 (EEST) http://staging.lexicum.net/mobile</span>
        </li>
        <li>
            <div class="qrcode"></div>
            <span>Wed Aug 05 2015 22:38:26 GMT+0300 (EEST) http://address-to-server/uploads/1438803506571/project-two.zip</span>
        </li>
        <li>
            <div class="qrcode"></div>
            <span>Wed Aug 05 2015 22:37:54 GMT+0300 (EEST) http://address-to-server/uploads/1438803506571/project-one.zip</span>
        </li>
    </ul>


Code & Libraries

- NodeJS
- ExpressJS http://expressjs.com
- QR code generator http://davidshimjs.github.io/qrcodejs/
- Heroku servers https://package-manager.herokuapp.com
- Github account https://github.com/dimitara/ppm.git 
- Sample app http://staging.weareathlon.com/athlon/qr/