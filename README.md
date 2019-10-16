# React File Upload

React frontend image upload with express backend server.js to handle file uploads. This is an excellent tutorial by [Traversy Media](http://www.traversymedia.com).

*** Note: to open web links in a new window use: _ctrl+click on link_**

## Table of contents

* [General info](#general-info)
* [Screenshots](#screenshots)
* [Technologies](#technologies)
* [Setup](#setup)
* [Features](#features)
* [Status](#status)
* [Inspiration](#inspiration)
* [Contact](#contact)

## General info

* Uploads an image file from the React frontend. This file is fetched by the backend using express.js and stored in  'uploads' in the public folder.

* The frontend uses a FileUpload component with a [FormData object](https://developer.mozilla.org/en-US/docs/Web/API/FormData/FormData) with inputs for the file itself and a file name. The image will be displayed on the frontend.

* Includes a % upload complete progress-bar component.

* Includes a dismissable status message component.

* [React hooks](https://reactjs.org/docs/hooks-overview.html#state-hook) used to write state. React extension shows hooks and their states in the dev console.

## Screenshots

![Example screenshot](./img/screen-shot.png).

## Technologies

* [Node.js v12.3.1](https://nodejs.org/) javascript runtime using the [Chrome V8 engine](https://v8.dev/)

* [Express middleware v4.17.1](https://expressjs.com/)

* [Express fileupload middleware v1.1.6-alpha.5](https://www.npmjs.com/package/express-fileupload)

* [React v16.10.2](https://reactjs.org/) Frontend javascript library.

* [Bootstrap front-end component library](https://getbootstrap.com/)

* [Font Awesome icons](https://fontawesome.com/)

* [React Hooks](https://reactjs.org/docs/hooks-overview.html#state-hook)

## Fullstack Dev Setup

### `npm run dev`

* Runs the front and backend simultaneously in development mode. It will open [http://localhost:3000](http://localhost:3000) to view in browser. Any code changes will automatically reload the browser.

## Code Examples

* FileUpload component try-catch to show percentage progress or error message.

```javascript
    try {
      const res = await axios.post('/upload', formData, {
        headers: {
          'Content-Type': 'multipart/form-data'
        },
        onUploadProgress: progressEvent => {
          setUploadPercentage(parseInt(Math.round((progressEvent.loaded * 100) / progressEvent.total)));
          setTimeout(() => setUploadPercentage(0), 10000);
        }
      });

      const { fileName, filePath } = res.data;
      setUploadedFile({ fileName, filePath });
      setMessage('File uploaded');
    } catch(err) {
      if(err.response.status === 500) {
        setMessage('There was a problem with the server');
      } else {
        setMessage(err.response.data.msg);
      }
    }
```

## Status & To-Do List

* Status: Completely updated oct 2019. Working full-stack image upload.

* To do: Add functionality.

## Inspiration

[Traversy Media: React File Uploader With Express (Using React Hooks)](https://www.youtube.com/watch?v=b6Oe2puTdMQ)

## Contact

Repo created by [ABateman](https://www.andrewbateman.org) - feel free to contact me!
