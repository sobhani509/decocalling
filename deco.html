<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Deco Calling</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Playfair+Display&display=swap');
    body {
      margin: 0;
      font-family: 'Arial', sans-serif;
      background-color: #f8f9fa;
    }
    .header {
      background-color: #2c3e50;
      padding: 16px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      text-align: center;
    }
    .header h1 {
      color: white;
      font-size: 2rem;
      font-family: 'Playfair Display', serif;
    }
    .container {
      display: flex;
      flex-direction: column;
      height: 100vh;
    }
    .home, .login, .call {
      display: none;
      flex: 1;
      align-items: center;
      justify-content: center;
      padding: 16px;
    }
    .show {
      display: flex;
    }
    .button {
      background-color: #3498db;
      color: white;
      font-weight: bold;
      padding: 12px 24px;
      border-radius: 24px;
      transition: background-color 0.3s ease-in-out;
      cursor: pointer;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    .button:hover {
      background-color: #2980b9;
    }
    .login input {
      width: 100%;
      padding: 12px;
      margin-bottom: 16px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 1rem;
    }
    .login button {
      width: 100%;
      background-color: #3498db;
      color: white;
      font-weight: bold;
      padding: 12px;
      border-radius: 24px;
      transition: background-color 0.3s ease-in-out;
      cursor: pointer;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    .login button:hover {
      background-color: #2980b9;
    }
    .call video {
      width: 100%;
      height: 100%;
      object-fit: cover;
      background-color: black;
    }
    .local-video {
      position: absolute;
      width: 120px;
      height: 160px;
      top: 20px;
      left: 20px;
      cursor: move;
    }
    .call-buttons {
      position: absolute;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      gap: 16px;
    }
    .call-buttons button {
      background-color: #3498db;
      color: white;
      font-weight: bold;
      padding: 12px 24px;
      border-radius: 24px;
      transition: background-color 0.3s ease-in-out;
      cursor: pointer;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    .call-buttons button:hover {
      background-color: #2980b9;
    }
    .call-buttons button:disabled {
      background-color: #7f8c8d;
      cursor: not-allowed;
    }
  </style>
</head>
<body>

<div class="container">
  <header class="header">
    <h1>Deco Calling</h1>
  </header>
  
  <!-- Home Page -->
  <div id="home" class="home show">
    <h1 class="text-5xl md:text-6xl font-playfair mb-8 text-[#2c3e50] text-center">Deco Calling</h1>
    <p class="text-xl md:text-2xl mb-12 text-[#34495e] font-light text-center">Elegant and simple video calls for everyone</p>
    <button class="button" onclick="showPage('login')">Get Started</button>
  </div>
  
  <!-- Login Page -->
  <div id="login" class="login">
    <h2 class="text-3xl md:text-4xl font-playfair mb-8 md:mb-12 text-[#2c3e50] text-center">Login to Deco Calling</h2>
    <form onsubmit="handleLogin(event)">
      <input type="text" id="username" name="username" placeholder="Username" required>
      <input type="password" id="password" name="password" placeholder="Password" required>
      <button type="submit">Login</button>
    </form>
  </div>
  
  <!-- Call Page -->
  <div id="call" class="call">
    <div id="remoteVideo" class="remote-video"></div>
    <div id="localVideo" class="local-video" onmousedown="handleDragStart(event)"></div>
    <div class="call-buttons">
      <button id="startCallBtn" onclick="startCall()" disabled>Start Call</button>
      <button onclick="answerCall()">Answer Call</button>
    </div>
  </div>
</div>

<script>
  let currentPage = 'home';
  let isLoggedIn = false;
  let localStream = null;
  let remoteStream = null;
  let peerConnection = null;
  let isCalling = false;

  function showPage(page) {
    document.getElementById(currentPage).classList.remove('show');
    document.getElementById(page).classList.add('show');
    currentPage = page;

    if (page === 'call' && isLoggedIn) {
      startLocalStream();
    }
  }

  function handleLogin(event) {
    event.preventDefault();
    const username = document.getElementById('username').value;
    const password = document.getElementById('password').value;
    
    if (username && password) {
      isLoggedIn = true;
      showPage('call');
      document.getElementById('startCallBtn').disabled = false;
    }
  }

  function startLocalStream() {
    navigator.mediaDevices.getUserMedia({ video: true, audio: true })
        .then(stream => {
            localStream = stream;
            const localVideo = document.getElementById('localVideo');
            localVideo.style.background = `url('${URL.createObjectURL(stream)}') center/cover no-repeat`;
            localVideo.srcObject = stream; // Use this for live video feed
        })
        .catch(error => {
            console.error('Error accessing media devices:', error);
            alert("Unable to access camera and microphone. Please check permissions.");
        });
  }


  function createPeerConnection() {
    peerConnection = new RTCPeerConnection();
    peerConnection.onicecandidate = event => {
      if (event.candidate) {
        console.error('New ICE candidate:', event.candidate);
      }
    };
    peerConnection.ontrack = event => {
      remoteStream = event.streams[0];
      document.getElementById('remoteVideo').style.background = `url('${URL.createObjectURL(remoteStream)}') center/cover no-repeat`;
    };
    localStream.getTracks().forEach(track => peerConnection.addTrack(track, localStream));
  }

  function startCall() {
    isCalling = true;
    createPeerConnection();
    peerConnection.createOffer()
      .then(offer => peerConnection.setLocalDescription(offer))
      .then(() => console.error('Offer:', peerConnection.localDescription))
      .catch(error => {
        console.error('Error creating offer:', error);
        isCalling = false;
      });
  }

  function answerCall(offer) {
    createPeerConnection();
    peerConnection.setRemoteDescription(new RTCSessionDescription(offer))
      .then(() => peerConnection.createAnswer())
      .then(answer => peerConnection.setLocalDescription(answer))
      .then(() => console.error('Answer:', peerConnection.localDescription))
      .catch(error => console.error('Error answering call:', error));
  }

  let dragOffsetX, dragOffsetY;
  function handleDragStart(event) {
    const localVideo = document.getElementById('localVideo');
    dragOffsetX = event.clientX - localVideo.offsetLeft;
    dragOffsetY = event.clientY - localVideo.offsetTop;
    document.addEventListener('mousemove', handleDrag);
    document.addEventListener('mouseup', handleDragEnd);
  }

  function handleDrag(event) {
    const localVideo = document.getElementById('localVideo');
    localVideo.style.left = `${event.clientX - dragOffsetX}px`;
    localVideo.style.top = `${event.clientY - dragOffsetY}px`;
  }

  function handleDragEnd() {
    document.removeEventListener('mousemove', handleDrag);
    document.removeEventListener('mouseup', handleDragEnd);
  }
</script>

</body>
</html>
