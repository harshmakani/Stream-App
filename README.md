This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

An application to Create, Update, Delete and List streams built in React/Redux.

[json-server](https://github.com/typicode/json-server) is used as an api server.

rtmpserver([node-media-server](https://github.com/illuspas/node-media-server)) helps to stream and I used [OBS](https://obsproject.com/) software to stream from my device.

For authentication, I have used [Google Oauth's](https://developers.google.com/api-client-library/javascript/features/authentication) client library for JavaScript.


## To run this application
1. Go to your terminal and run `mkdir streams`
1. `cd streams`
1. `git clone https://github.com/harshmakani/stream-app.git`
1. `cd stream-app`
1. `npm install`: This will setup the react application. Now we need to setup api server.
1. `cd ..`
1. `git clone https://github.com/harshmakani/stream-app-json-server.git`
1. `cd stream-app-json-server`
1. `npm install`: This will setup the api server. Now we need to setup rtmpserver
1. `cd ..`
1. `git clone https://github.com/harshmakani/rtmp-server.git`
1. `cd rtmp-server`
1. `npm install`
1. Now start all three applications by navigating into those directories and running `npm start`

Now once the applications are running, you can see that there are no list of streams at this moment. Try to login with google and once you are logged in, you can create a stream. Logged in users can modify/delete a stream.

Once a stream is created, you can view the stream by clicking on the stream title, here you will see in navigation bar the stream-id. If this is your first stream then the id must be 1, remember this id as it will be used as `Stream Key` while streaming. Right now the video player will only show loading spinner as there is no one who is streaming.

To start streaming: 
1. Open your OBS software and click on the bottom left (+) plus sign and create a new Scene.
1. Now just besides the Scene block, there is Sources block. Click on (+) plus sign again and you can choose to share your screen, Audio, Video, etc sources from your device. Add relevant sources you want to stream.
1. Now click on `Settings` button on the very right column called Controls.
1. Go to `Stream` tab
1. In `Service` choose `Custom...`
1. In `Server` type `rtmp://localhost/live`
1. In `Stream Key` put the stream-id that was created when the stream was created. For our case here it should be `1`.
1. Click `OK`
1. Click `Start Streaming` button located in the same column where `Settings` button was.

That's it! Navigate back to your client application and you can see the stream now.


## Application Overview
This application focuses on CRUD operations with respect to React/Redux and how to stream from your device.
The client application uses axios for making network requests, react-router-dom for navigation, redux for state management, redux-form to link forms directly with redux and redux-thunk as a middleware for redux. I have also used lodash for easing some operations with respect to data manipulation. 
