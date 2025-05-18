<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>fourtyfivezone - Social Media for SMK 45</title>
<style>
  /* Reset & basics */
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #0d1117;
    color: #c9d1d9;
    display: flex;
    min-height: 100vh;
    overflow-x: hidden;
  }
  a {
    color: inherit;
    text-decoration: none;
  }
  /* Sidebar */
  .sidebar {
    width: 80px;
    background-color: #161b22;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 1rem 0;
    border-right: 1px solid #30363d;
  }
  /* SMK 45 logo stylized */
  .sidebar .smk-logo {
    width: 48px;
    height: 48px;
    margin-bottom: 1rem;
    border-radius: 50%;
    background: linear-gradient(135deg, #0a74da, #004b91);
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 900;
    font-size: 1.1rem;
    color: white;
    user-select: none;
    box-shadow: 0 0 8px #0a74dacc;
  }
  .sidebar .logo {
    font-size: 1.4rem;
    font-weight: 700;
    color: #58a6ff;
    margin-bottom: 2rem;
    user-select: none;
  }
  .sidebar button {
    background: none;
    border: none;
    color: #8b949e;
    margin: 1rem 0;
    cursor: pointer;
    font-size: 1.8rem;
    transition: color 0.2s ease-in-out;
  }
  .sidebar button:hover {
    color: #58a6ff;
  }
  /* Main Content */
  .main {
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    max-width: 700px;
    border-right: 1px solid #30363d;
  }
  header {
    position: sticky;
    top: 0;
    background: #161b22;
    padding: 1rem 1.5rem;
    border-bottom: 1px solid #30363d;
    display: flex;
    align-items: center;
    gap: 0.8rem;
  }
  /* SMK 45 logo stylized in header */
  .header-smk-logo {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: linear-gradient(135deg, #0a74da, #004b91);
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 900;
    font-size: 1rem;
    color: white;
    user-select: none;
    box-shadow: 0 0 6px #0a74dacc;
  }
  header h1 {
    font-size: 1.5rem;
    margin: 0;
    color: #58a6ff;
    font-weight: 800;
    user-select: none;
  }
  /* Post composer */
  .post-composer {
    padding: 1rem 1.5rem;
    border-bottom: 1px solid #30363d;
  }
  .post-composer textarea {
    width: 100%;
    resize: none;
    border-radius: 12px;
    padding: 0.8rem 1rem;
    font-size: 1rem;
    background-color: #0d1117;
    border: 1px solid #30363d;
    color: #c9d1d9;
    min-height: 70px;
    transition: border-color 0.2s ease-in-out;
  }
  .post-composer textarea:focus {
    outline: none;
    border-color: #58a6ff;
    background-color: #161b22;
  }
  .post-composer .actions {
    margin-top: 0.5rem;
    display: flex;
    justify-content: flex-end;
  }
  .post-composer button {
    background-color: #238636;
    color: #ffffff;
    border: none;
    padding: 0.5rem 1.1rem;
    border-radius: 9999px;
    font-weight: 600;
    cursor: pointer;
    opacity: 0.7;
    transition: opacity 0.2s ease-in-out, background-color 0.2s ease-in-out;
  }
  .post-composer button:enabled {
    opacity: 1;
  }
  .post-composer button:hover:enabled {
    background-color: #2ea043;
  }
  /* Feed */
  .feed {
    flex-grow: 1;
    overflow-y: auto;
    padding: 1rem 1.5rem;
  }
  .post {
    background-color: #161b22;
    border-radius: 12px;
    padding: 1rem 1rem 1.2rem;
    margin-bottom: 1rem;
    box-shadow: 0 1px 3px rgb(0 0 0 / 0.5);
    transition: background-color 0.2s ease-in-out;
  }
  .post:hover {
    background-color: #21262d;
  }
  .post-header {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 0.5rem;
  }
  .avatar {
    width: 42px;
    height: 42px;
    border-radius: 50%;
    background-color: #58a6ff;
    color: #0d1117;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    font-size: 1.2rem;
    user-select: none;
  }
  .post-user-info {
    display: flex;
    flex-direction: column;
  }
  .post-name {
    font-weight: 700;
    font-size: 1rem;
    color: #58a6ff;
  }
  .post-username {
    font-size: 0.85rem;
    color: #8b949e;
  }
  .post-content {
    font-size: 1rem;
    line-height: 1.4;
    white-space: pre-wrap;
  }
  /* Right sidebar */
  .rightbar {
    width: 280px;
    background-color: #161b22;
    padding: 1rem 1.5rem;
    color: #8b949e;
    display: flex;
    flex-direction: column;
  }
  .rightbar h2 {
    font-weight: 700;
    color: #58a6ff;
    margin-top: 0;
    margin-bottom: 1rem;
  }
  .rightbar p {
    font-size: 0.9rem;
    line-height: 1.4;
  }
  /* Scrollbar for feed */
  .feed::-webkit-scrollbar {
    width: 8px;
  }
  .feed::-webkit-scrollbar-track {
    background: transparent;
  }
  .feed::-webkit-scrollbar-thumb {
    background-color: #30363d;
    border-radius: 9999px;
  }
  /* Responsive */
  @media (max-width: 900px) {
    body {
      flex-direction: column;
    }
    .sidebar, .rightbar {
      display: none;
    }
    .main {
      max-width: 100%;
      border: none;
    }
  }
</style>
</head>
<body>
  <nav class="sidebar" aria-label="Primary">
    <div class="smk-logo" title="SMK 45 Logo">45</div>
    <div class="logo" title="fourtyfivezone">45Z</div>
    <button title="Home" aria-label="Home">&#8962;</button>
    <button title="Search" aria-label="Search">&#128269;</button>
    <button title="Notifications" aria-label="Notifications">&#128276;</button>
    <button title="Messages" aria-label="Messages">&#9993;</button>
    <button title="Profile" aria-label="Profile">&#128100;</button>
  </nav>

  <main class="main" role="main" aria-label="Main content">
    <header>
      <div class="header-smk-logo" title="SMK 45 Logo">45</div>
      <h1>fourtyfivezone</h1>
    </header>
    <section class="post-composer" aria-label="Create new post">
      <textarea id="postInput" placeholder="Apa yang kamu pikirkan, SMK 45?" maxlength="280" aria-multiline="true" aria-label="Post content"></textarea>
      <div class="actions">
        <button id="postBtn" disabled>Post</button>
      </div>
    </section>
    <section class="feed" id="feed" aria-live="polite" aria-relevant="additions">
      <!-- Posts will appear here -->
    </section>
  </main>

  <aside class="rightbar" aria-label="About fourtyfivezone">
    <h2>fourtyfivezone</h2>
    <p>Sosial media khusus murid dan guru SMK 45. Bagikan cerita, informasi, dan kabar terbaru seputar sekolahmu!</p>
    <p><strong>Tip:</strong> Gunakan bahasa yang sopan dan hormati sesama pengguna.</p>
  </aside>

<script>
  // Enable/disable post button based on textarea content
  const postInput = document.getElementById('postInput');
  const postBtn = document.getElementById('postBtn');
  const feed = document.getElementById('feed');

  postInput.addEventListener('input', () => {
    postBtn.disabled = postInput.value.trim().length === 0;
  });

  // Sample user data for demo posts
  const users = [
    { name: 'Budi Santoso', username: 'budi_smk45' },
    { name: 'Sari Wijaya', username: 'sari_guru' },
    { name: 'Tia Nurul', username: 'tia_smk45' }
  ];

  // Function to create a post element
  function createPostElement(name, username, content) {
    const post = document.createElement('article');
    post.className = 'post';

    const postHeader = document.createElement('div');
    postHeader.className = 'post-header';

    const avatar = document.createElement('div');
    avatar.className = 'avatar';
    // Initials from name
    avatar.textContent = name.split(' ').map(n => n[0]).join('').toUpperCase();

    const userInfo = document.createElement('div');
    userInfo.className = 'post-user-info';

    const displayName = document.createElement('span');
    displayName.className = 'post-name';
    displayName.textContent = name;

    const userTag = document.createElement('span');
    userTag.className = 'post-username';
    userTag.textContent = '@' + username;

    userInfo.appendChild(displayName);
    userInfo.appendChild(userTag);

    postHeader.appendChild(avatar);
    postHeader.appendChild(userInfo);

    const postContent = document.createElement('p');
    postContent.className = 'post-content';
    postContent.textContent = content;

    post.appendChild(postHeader);
    post.appendChild(postContent);

    return post;
  }

  // Add initial sample posts
  const initialPosts = [
    { name: 'Budi Santoso', username: 'budi_smk45', content: 'Halo semuanya! Selamat datang di fourtyfivezone, tempat kita berbagi cerita SMK 45.' },
    { name: 'Sari Wijaya', username: 'sari_guru', content: 'Jangan lupa konsultasi tugasmu di sini ya, guru dan murid bisa saling membantu!' },
    { name: 'Tia Nurul', username: 'tia_smk45', content: 'Siap-siap untuk acara OSIS minggu depan, jangan sampai ketinggalan!' }
  ];

  initialPosts.forEach(p => {
    const postEl = createPostElement(p.name, p.username, p.content);
    feed.appendChild(postEl);
  });

  // Handle posting new content
  postBtn.addEventListener('click', () => {
    const content = postInput.value.trim();
    if(content.length === 0) return;
    // For demo, use a fixed user - you could extend this later with login etc.
    const newPost = createPostElement('You', 'you_smk45', content);
    feed.insertBefore(newPost, feed.firstChild);
    postInput.value = '';
    postBtn.disabled = true;
  });
</script>
</body>
</html>


