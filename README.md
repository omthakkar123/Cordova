1.  Hello World App,
    Buttons,
    Event Listeners

        Command
        =======
        cordova create prac1 io.cordova.prac Hello
        cd prac1
        cordova platform add android
        cordova build android
        cordova emulate android

        HTML
        ====
        <html>
        <head>
            <title>Hello, World!</title>
        </head>
        <body>
            <h1>Hello, World!</h1>
            <button id="alertBtn">ALERT!</button>
            <script src="cordova.js"></script>
            <script src="js/index.js"></script>
            <script>
                document.getElementById("alertBtn").addEventListener("click",alertFunction);
                function alertFunction(){
                    alert("This Is Alert Message!");
                }
            </script>
        </body>
        </html>

2.  Functions,
    Events,
    Handling Back Button

        Command
        =======
        cordova create prac2 io.cordova.prac Hello
        cd prac2
        cordova platform add android
        cordova build android
        cordova emulate android

        HTML
        ====
        <html>
        <head>
            <title>Functions</title>
        </head>
        <body>
            <h1>Events</h1>
            <button id="alertBtn">ALERT!</button>
            <script src="cordova.js"></script>
            <script src="js/index.js"></script>
            <script>
                document.getElementById("alertBtn").addEventListener("click",alertFunction);
                document.addEventListener("backbutton", onBackKeyDown, false);  
                function onBackKeyDown(e) { 
                    e.preventDefault(); 
                    alert('Back Button is Pressed!'); 
                }
                function alertFunction(){
                    alert("This Is Alert Message!");
                }
            </script>
        </body>
        </html>

3.  Plugins,
    Battery Plugin,
    Camera Plugin
    
        Command
        =======
        cordova create prac3 io.cordova.prac Hello
        cd prac3
        cordova platform add android
        cordova plugin add cordova-plugin-battery-status
        cordova plugin add cordova-plugin-camera
        cordova build android
        cordova emulate android

        HTML
        ====
        <html>
        <head>
            <title>Plugins</title>
        </head>
        <body>
            <h1>Plugins</h1>
            <button id = "cameraTakePicture">TAKE PICTURE</button>
            <img id = "myImage"></img>
            <script src="cordova.js"></script>
            <script src="js/index.js"></script>
            <script>
                window.addEventListener("batterystatus", onBatteryStatus, false); 
                function onBatteryStatus(info) { 
                    alert("BATTERY STATUS:  Level: " + info.level + " isPlugged: " + info.isPlugged); 
                }
                document.getElementById("cameraTakePicture").addEventListener 
                    ("click", cameraTakePicture); 
                function cameraTakePicture() { 
                    navigator.camera.getPicture(onSuccess, onFail, {  
                        quality: 50, 
                        destinationType: Camera.DestinationType.DATA_URL 
                    });
                    function onSuccess(imageData) { 
                        var image = document.getElementById('myImage'); 
                        image.src = "data:image/jpeg;base64," + imageData; 
                    }  
                    function onFail(message) { 
                        alert('Failed because: ' + message); 
                    } 
                }
            </script>
        </body>
        </html>

4.  Contacts Plugin,
    Device Plugin,
    Accelerometer Plugin

        Command
        =======
        cordova create prac4 io.cordova.prac Hello
        cd prac4
        cordova platform add android
        cordova plugin add cordova-plugin-contacts
        cordova plugin add cordova-plugin-device
        cordova plugin add cordova-plugin-device-motion
        cordova build android
        cordova emulate android

        HTML
        ====
        <html>
        <head>
            <title>Plugins</title>
        </head>
        <body>
            <h1>Plugins</h1>
            <button id = "createContact">ADD CONTACT</button>
            <button id = "cordovaDevice">CORDOVA DEVICE</button>
            <button id = "getAcceleration">GET ACCELERATION</button>
            <script src="cordova.js"></script>
            <script src="js/index.js"></script>
            <script>
                document.getElementById("createContact").addEventListener("click", createContact);
                document.getElementById("cordovaDevice").addEventListener("click", cordovaDevice);
                document.getElementById("getAcceleration").addEventListener("click", getAcceleration);
                function createContact() {
                    var myContact = navigator.contacts.create({"displayName": "Test User"});
                    myContact.save(contactSuccess, contactError);
                    function contactSuccess() {
                        alert("Contact is saved!");
                    } 
                    function contactError(message) {
                        alert('Failed because: ' + message);
                    }   
                }
                function cordovaDevice() {
                    alert("Cordova version: " + device.cordova + "\n" +
                        "Device model: " + device.model + "\n" +
                        "Device platform: " + device.platform + "\n" +
                        "Device UUID: " + device.uuid + "\n" +
                        "Device version: " + device.version);
                }
                function getAcceleration() {
                    navigator.accelerometer.getCurrentAcceleration(
                        accelerometerSuccess, accelerometerError);
                    function accelerometerSuccess(acceleration) {
                        alert('Acceleration X: ' + acceleration.x + '\n' +
                            'Acceleration Y: ' + acceleration.y + '\n' +
                            'Acceleration Z: ' + acceleration.z + '\n' +
                            'Timestamp: '      + acceleration.timestamp + '\n');
                    };
                    function accelerometerError() {
                        alert('onError!');
                    };
                }
            </script>
        </body>
        </html>

5.  Device Orientation Plugin,
    Prompt Function

        Command
        =======
        cordova create prac5 io.cordova.prac Hello
        cd prac5
        cordova platform add android
        cordova plugin add cordova-plugin-device-orientation
        cordova build android
        cordova emulate android

        HTML
        ====
        <html>
        <head>
            <title>Plugins</title>
        </head>
        <body>
            <h1>Plugins</h1>
            <button id = "getOrientation">GET ORIENTATION</button>
            <button id = "getPrompt">PROMPT</button>
            <script src="cordova.js"></script>
            <script src="js/index.js"></script>
            <script>
                document.getElementById("getOrientation").addEventListener("click", getOrientation);
                document.getElementById("getPrompt").addEventListener("click", getPrompt)
                function getOrientation() {
                    navigator.compass.getCurrentHeading(compassSuccess, compassError);
                    function compassSuccess(heading) {
                        alert('Heading: ' + heading.magneticHeading);
                    };
                    function compassError(error) {
                        alert('CompassError: ' + error.code);
                    };
                }
                function getPrompt(){
                    var a = prompt("Enter Number");
                    alert(a);
                }
            </script>
        </body>
        </html>

6.  File Plugin,
    File Transfer Plugin
    
        Command
        =======
        cordova create prac6 io.cordova.prac Hello
        cd prac6
        cordova platform add android
        cordova plugin add cordova-plugin-file
        cordova plugin add cordova-plugin-file-transfer
        cordova build android
        cordova emulate android

        HTML
        ====
        <html>
        <head>
            <title>Plugins</title>
        </head>
        <body>
            <h1>Plugins</h1>
            <button id = "createFile">CREATE FILE</button>
            <button id = "writeFile">WRITE FILE</button>
            <button id = "readFile">READ FILE</button>
            <button id = "removeFile">DELETE FILE</button>
            <button id = "uploadFile">UPLOAD</button>
            <button id = "downloadFile">DOWNLOAD</button>
            <textarea id = "textarea"></textarea>
            <script src="cordova.js"></script>
            <script src="js/index.js"></script>
            <script>
                document.getElementById("createFile").addEventListener("click", createFile);
                document.getElementById("writeFile").addEventListener("click", writeFile);
                document.getElementById("readFile").addEventListener("click", readFile);
                document.getElementById("removeFile").addEventListener("click", removeFile);
                document.getElementById("uploadFile").addEventListener("click", uploadFile);
                document.getElementById("downloadFile").addEventListener("click", downloadFile);
                function createFile() {
                    var type = window.TEMPORARY;
                    var size = 5*1024*1024;
                    window.requestFileSystem(type, size, successCallback, errorCallback)
                    function successCallback(fs) {
                        fs.root.getFile('log.txt', {create: true, exclusive: true}, function(fileEntry) {
                            alert('File creation successfull!')
                        }, errorCallback);
                    }
                    function errorCallback(error) {
                        alert("ERROR: " + error.code)
                    }
                }
                function writeFile() {
                    var type = window.TEMPORARY;
                    var size = 5*1024*1024;
                    window.requestFileSystem(type, size, successCallback, errorCallback)
                    function successCallback(fs) {
                        fs.root.getFile('log.txt', {create: true}, function(fileEntry) {
                            fileEntry.createWriter(function(fileWriter) {
                                fileWriter.onwriteend = function(e) {
                                alert('Write completed.');
                                };
                                fileWriter.onerror = function(e) {
                                alert('Write failed: ' + e.toString());
                                };
                                var blob = new Blob(['Lorem Ipsum'], {type: 'text/plain'});
                                fileWriter.write(blob);
                            }, errorCallback);
                        }, errorCallback);
                    }
                    function errorCallback(error) {
                        alert("ERROR: " + error.code)
                    }
                }
                function readFile() {
                    var type = window.TEMPORARY;
                    var size = 5*1024*1024;
                    window.requestFileSystem(type, size, successCallback, errorCallback);
                    function successCallback(fs) {
                        fs.root.getFile('log.txt', {}, function(fileEntry) {
                            fileEntry.file(function(file) {
                                var reader = new FileReader();
                                reader.onloadend = function(e) {
                                var txtArea = document.getElementById('textarea');
                                txtArea.value = this.result;
                                };
                                reader.readAsText(file);
                            }, errorCallback);
                        }, errorCallback);
                    }
                    function errorCallback(error) {
                        alert("ERROR: " + error.code)
                    }
                }	
                function removeFile() {
                    var type = window.TEMPORARY;
                    var size = 5*1024*1024;
                    window.requestFileSystem(type, size, successCallback, errorCallback);
                    function successCallback(fs) {
                        fs.root.getFile('log.txt', {create: false}, function(fileEntry) {

                            fileEntry.remove(function() {
                                alert('File removed.');
                            }, errorCallback);
                        }, errorCallback);
                    }
                    function errorCallback(error) {
                        alert("ERROR: " + error.code)
                    }
                }	
                function downloadFile() {
                    var fileTransfer = new FileTransfer();
                    var uri = encodeURI("http://s14.postimg.org/i8qvaxyup/bitcoin1.jpg");
                    var fileURL =  "///storage/emulated/0/DCIM/myFile";
                    fileTransfer.download(
                        uri, fileURL, function(entry) {
                            console.log("download complete: " + entry.toURL());
                        },
                        function(error) {
                            console.log("download error source " + error.source);
                            console.log("download error target " + error.target);
                            console.log("download error code" + error.code);
                        },
                        false, {
                            headers: {
                                "Authorization": "Basic dGVzdHVzZXJuYW1lOnRlc3RwYXNzd29yZA=="
                            }
                        }
                    );
                }
                function uploadFile() {
                    var fileURL = "///storage/emulated/0/DCIM/myFile"
                    var uri = encodeURI("http://posttestserver.com/post.php");
                    var options = new FileUploadOptions();
                    options.fileKey = "file";
                    options.fileName = fileURL.substr(fileURL.lastIndexOf('/')+1);
                    options.mimeType = "text/plain";
                    var headers = {'headerParam':'headerValue'};
                    options.headers = headers;
                    var ft = new FileTransfer();
                    ft.upload(fileURL, uri, onSuccess, onError, options);
                    function onSuccess(r) {
                        console.log("Code = " + r.responseCode);
                        console.log("Response = " + r.response);
                        console.log("Sent = " + r.bytesSent);
                    }
                    function onError(error) {
                        alert("An error has occurred: Code = " + error.code);
                        console.log("upload error source " + error.source);
                        console.log("upload error target " + error.target);
                    }  
                }
            </script>
        </body>
        </html>

7.  Globalization Plugin,
    Media Plugin,
    Media Capture Plugin

        Command
        =======
        cordova create prac7 io.cordova.prac Hello
        cd prac7
        cordova platform add android
        cordova plugin add cordova-plugin-globalization
        cordova plugin add cordova-plugin-media
        cordova plugin add cordova-plugin-media-capture
        cordova build android
        cordova emulate android

        HTML
        ====
        <html>
        <head>
            <title>Plugins</title>
        </head>
        <body>
            <h1>Plugins</h1>
            <button id = "getLanguage">LANGUAGE</button>
            <button id = "getLocaleName">LOCALE NAME</button>
            <button id = "getDate">DATE</button>
            <button id = "getCurrency">CURRENCY</button>
            <button id = "playAudio">PLAY</button>
            <button id = "pauseAudio">PAUSE</button>
            <button id = "stopAudio">STOP</button>
            <button id = "volumeUp">VOLUME UP</button>
            <button id = "volumeDown">VOLUME DOWN</button>
            <button id = "audioCapture">AUDIO</button>
            <button id = "imageCapture">IMAGE</button>
            <button id = "videoCapture">VIDEO</button>
            <script src="cordova.js"></script>
            <script src="js/index.js"></script>
            <script>
                document.getElementById("getLanguage").addEventListener("click", getLanguage);
                document.getElementById("getLocaleName").addEventListener("click", getLocaleName);
                document.getElementById("getDate").addEventListener("click", getDate);
                document.getElementById("getCurrency").addEventListener("click", getCurrency);
                document.getElementById("playAudio").addEventListener("click", playAudio);
                document.getElementById("pauseAudio").addEventListener("click", pauseAudio);
                document.getElementById("stopAudio").addEventListener("click", stopAudio);
                document.getElementById("volumeUp").addEventListener("click", volumeUp);
                document.getElementById("volumeDown").addEventListener("click", volumeDown);
                document.getElementById("audioCapture").addEventListener("click", audioCapture);
                document.getElementById("imageCapture").addEventListener("click", imageCapture);
                document.getElementById("videoCapture").addEventListener("click", videoCapture);
                function getLanguage() {
                    navigator.globalization.getPreferredLanguage(onSuccess, onError);
                    function onSuccess(language) {
                        alert('language: ' + language.value + '\n');
                    }
                    function onError(){
                        alert('Error getting language');
                    }
                }
                function getLocaleName() {
                    navigator.globalization.getLocaleName(onSuccess, onError);
                    function onSuccess(locale) {
                        alert('locale: ' + locale.value);
                    }
                    function onError(){
                        alert('Error getting locale');
                    }
                }
                function getDate() {
                    var date = new Date();
                    var options = {
                        formatLength:'short',
                        selector:'date and time'
                    }
                    navigator.globalization.dateToString(date, onSuccess, onError, options);
                    function onSuccess(date) {
                        alert('date: ' + date.value);
                    }
                    function onError(){
                        alert('Error getting dateString');
                    }
                }
                function getCurrency() {
                    var currencyCode = 'EUR';
                    navigator.globalization.getCurrencyPattern(currencyCode, onSuccess, onError);
                    function onSuccess(pattern) {
                        alert('pattern: '  + pattern.pattern  + '\n' +
                            'code: '     + pattern.code     + '\n' +
                            'fraction: ' + pattern.fraction + '\n' +
                            'rounding: ' + pattern.rounding + '\n' +
                            'decimal: '  + pattern.decimal  + '\n' +
                            'grouping: ' + pattern.grouping);
                    }
                    function onError(){
                        alert('Error getting pattern');
                    }
                }
                var myMedia = null;
                function playAudio() {
                    var src = "/android_asset/www/audio/piano.mp3";
                    if(myMedia === null) {
                        myMedia = new Media(src, onSuccess, onError);

                        function onSuccess() {
                            console.log("playAudio Success");
                        }

                        function onError(error) {
                            console.log("playAudio Error: " + error.code);
                        }
                    }
                    myMedia.play();
                }
                function pauseAudio() {
                    if(myMedia) {
                        myMedia.pause();
                    }
                }
                function stopAudio() {
                    if(myMedia) {
                        myMedia.stop(); 
                    }
                    myMedia = null;
                }
                var volumeValue = 0.5;
                function volumeUp() {
                    if(myMedia && volumeValue < 1) {
                        myMedia.setVolume(volumeValue += 0.1);
                    }
                }
                function volumeDown() {
                    if(myMedia && volumeValue > 0) {
                        myMedia.setVolume(volumeValue -= 0.1);
                    }
                }
                function audioCapture() {
                    var options = {
                        limit: 1,
                        duration: 10
                    };
                    navigator.device.capture.captureAudio(onSuccess, onError, options);
                    function onSuccess(mediaFiles) {
                        var i, path, len;
                        for (i = 0, len = mediaFiles.length; i < len; i += 1) {
                            path = mediaFiles[i].fullPath;
                            console.log(mediaFiles);
                        }
                    }
                    function onError(error) {
                        navigator.notification.alert('Error code: ' + error.code, null, 'Capture Error');
                    }
                }
                function imageCapture() {
                    var options = {
                        limit: 1
                    };
                    navigator.device.capture.captureImage(onSuccess, onError, options);
                    function onSuccess(mediaFiles) {
                        var i, path, len;
                        for (i = 0, len = mediaFiles.length; i < len; i += 1) {
                            path = mediaFiles[i].fullPath;
                            console.log(mediaFiles);
                        }
                    }
                    function onError(error) {
                        navigator.notification.alert('Error code: ' + error.code, null, 'Capture Error');
                    }
                }
                function videoCapture() {
                    var options = {
                        limit: 1,
                        duration: 10
                    };
                    navigator.device.capture.captureVideo(onSuccess, onError, options);
                    function onSuccess(mediaFiles) {
                        var i, path, len;
                        for (i = 0, len = mediaFiles.length; i < len; i += 1) {
                            path = mediaFiles[i].fullPath;
                            console.log(mediaFiles);
                        }
                    }
                    function onError(error) {
                        navigator.notification.alert('Error code: ' + error.code, null, 'Capture Error');
                    }
                }
            </script>
        </body>
        </html>

8.  Network Information Plugin,
    Splash Screen Plugin,
    Vibration Plugin

        Command
        =======
        cordova create prac8 io.cordova.prac Hello
        cd prac8
        cordova platform add android
        cordova plugin add cordova-plugin-network-information
        cordova plugin add cordova-plugin-splashscreen
        cordova plugin add cordova-plugin-vibration
        cordova build android
        cordova emulate android

        HTML
        ====
        <html>
        <head>
            <preference name = "SplashScreen" value = "screen" />
            <preference name = "SplashScreenDelay" value = "3000" />
            <preference name = "SplashMaintainAspectRatio" value = "true" />
            <title>Plugins</title>
        </head>
        <body>
            <h1>Plugins</h1>
            <button id = "networkInfo">INFO</button>
            <button id = "vibration">VIBRATION</button>
            <button id = "vibrationPattern">PATTERN</button>
            <script src="cordova.js"></script>
            <script src="js/index.js"></script>
            <script>
                document.getElementById("networkInfo").addEventListener("click", networkInfo);
                document.addEventListener("offline", onOffline, false);
                document.addEventListener("online", onOnline, false);
                document.getElementById("vibration").addEventListener("click", vibration);
                document.getElementById("vibrationPattern").addEventListener("click", vibrationPattern);
                function networkInfo() {
                    var networkState = navigator.connection.type;
                    var states = {};
                    states[Connection.UNKNOWN]  = 'Unknown connection';
                    states[Connection.ETHERNET] = 'Ethernet connection';
                    states[Connection.WIFI]     = 'WiFi connection';
                    states[Connection.CELL_2G]  = 'Cell 2G connection';
                    states[Connection.CELL_3G]  = 'Cell 3G connection';
                    states[Connection.CELL_4G]  = 'Cell 4G connection';
                    states[Connection.CELL]     = 'Cell generic connection';
                    states[Connection.NONE]     = 'No network connection';
                    alert('Connection type: ' + states[networkState]);
                }
                function onOffline() {
                    alert('You are now offline!');
                }
                function onOnline() {
                    alert('You are now online!');
                }
                function vibration() {
                    var time = 3000;
                    navigator.vibrate(time);
                }
                function vibrationPattern() {
                    var pattern = [1000, 1000, 1000, 1000];
                    navigator.vibrate(pattern);
                }
            </script>
        </body>
        </html>

9.  Single Page Apps,
    Multipage Apps,
    Store Data Locally

        Command
        =======
        cordova create prac9 io.cordova.prac Hello
        cd prac9
        cordova platform add android
        cordova build android
        cordova emulate android

        HTML
        ====
        <html>
        <head>
            <title>Plugins</title>
        </head>
        <body>
            <h1>Plugins</h1>
            <button id = "setLocalStorage">SET LOCAL STORAGE</button>
            <button id = "showLocalStorage">SHOW LOCAL STORAGE</button>
            <button id = "removeProjectFromLocalStorage">REMOVE PROJECT</button>
            <button id = "getLocalStorageByKey">GET BY KEY</button>
            <script src="cordova.js"></script>
            <script src="js/index.js"></script>
            <script>
                document.getElementById("setLocalStorage").addEventListener("click", setLocalStorage); 
                document.getElementById("showLocalStorage").addEventListener("click", showLocalStorage); 
                document.getElementById("removeProjectFromLocalStorage").addEventListener("click", removeProjectFromLocalStorage); 
                document.getElementById("getLocalStorageByKey").addEventListener("click", getLocalStorageByKey);  
                var localStorage = window.localStorage; 
                function setLocalStorage() { 
                    localStorage.setItem("Name", "John"); 
                    localStorage.setItem("Job", "Developer"); 
                    localStorage.setItem("Project", "Cordova Project"); 
                }
                function showLocalStorage() { 
                    console.log(localStorage.getItem("Name")); 
                    console.log(localStorage.getItem("Job")); 
                    console.log(localStorage.getItem("Project")); 
                } 	
                function removeProjectFromLocalStorage() {
                    localStorage.removeItem("Project");
                }
                function getLocalStorageByKey() {
                    console.log(localStorage.key(0));
                }
            </script>
        </body>
        </html>

10. SQLite Plugin,
    SQLite Read/Write & Search,
    SQLite Storage With JQuery
