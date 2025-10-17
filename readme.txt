VR Video Menu Prototype – README

Overview:
This project is a browser-based VR prototype built with A-Frame.
It allows users to select from a list of 360° videos inside a VR menu and view them inside a virtual room.
Optional background music can play in both the menu and individual rooms.

The prototype works in desktop mode and in VR headsets.
All content (videos, audio, JSON configuration) is stored locally and loaded dynamically.

Hosting on Netlify:
Netlify is recommended because it supports large static files (such as MP4 video content).
To deploy:

- Option 1: Drag & Drop
    1. Create a free account at https://www.netlify.com/
    2. Prepare your project folder (the folder must contain your index.html)
    3. Drag & drop the folder into the Netlify Drop section (can be found on the dashboard under “Deploy manually”)
    4. Netlify will generate a public link automatically

- Option 2: Git Integration
    1. Push your project folder to GitHub or GitLab
    2. Connect the repository in Netlify under New Site → Import from Git
    3. Set the deployment folder to the root directory
    4. Deploy. Netlify will host it instantly

Important:
- All file paths in your project must stay the same as in your folder structure
- Videos and audio files should stay in the same relative paths (e.g. /media/)

File Formats
Videos: .mp4 (equirectangular format) -> This is important so that the video wraps correctly around the sphere (360 view). The most common format is "equirectangular 2:1".
Music / Audio:	.mp3 ->	Used as optional background music for menu or rooms.


Configuring Videos in videos.json:
The file videos.json controls the menu and room content.
You can add any number of items. Each video entry looks like this:

{
  "id": 1,
  "title": "Sample Video",
  "src": "media/video1.mp4",
  "music": "media/music1.mp3"
}

Explanation:
- id: Must be unique. Start at 1 and count up (1, 2, 3...).
- title: The name that will be shown under the icon in the menu.
- src: Path to the MP4 video file. Make sure the file exists in your project folder.
- music	(Optional): Path to the MP3 music file that plays inside this video room. (You can remove the music field if you don’t want audio for that video)

At the top under menuMusic, you can implement the music for the menu.
You can add as many vidoes as you like, the menu will adapt automatically (max 4 rows, unlimited icons per row).

Folder Structure (Recommended)
project-folder/
│
├── index.html
├── videos.json
├── media/
│   ├── video1.mp4
│   ├── video2.mp4
│   ├── music1.mp3
│   ├── menuMusic.mp3
│   └── videoicon.png
└── models/
    └── man_sitting.glb


How to Run Locally Before Uploading:
- Keep all files in the correct folders
- Upload project to Netlify 
- Open the project in the browser

VR Controls:
- Look at an icon for 3 seconds to open the despired room
- In a video room, look upwards at the invisible return zone to go back to the menu
    - After 2 seconds the loading ring becomes visible
    - After a total of 5 seconds, it returns automatically
