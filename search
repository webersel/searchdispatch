<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Search Page</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            background-image: url('https://www.shutterstock.com/image-illustration/orangepurple-gradient-against-stunning-sunset-260nw-1275739732.jpg');
            background-size: cover;
            font-family: Arial, sans-serif;
            position: relative;
            overflow: hidden;
        }
        .tab-container {
            width: 100%;
            background-color: #333;
            display: flex;
            justify-content: center;
            position: relative;
            z-index: 2;
        }
        .tab {
            padding: 14px 20px;
            cursor: pointer;
            color: white;
            background-color: #333;
            border: none;
            outline: none;
            transition: background-color 0.3s;
        }
        .tab:hover {
            background-color: #555;
        }
        .tab.active {
            background-color: #666;
        }
        .tab-close {
            margin-left: 10px;
            color: red;
            cursor: pointer;
            display: inline-block;
        }
        .add-tab-button {
            padding: 14px 20px;
            cursor: pointer;
            color: white;
            background-color: green;
            border: none;
            outline: none;
            transition: background-color 0.3s;
        }
        .add-tab-button:hover {
            background-color: darkgreen;
        }
        .search-container {
            position: relative;
            display: flex;
            flex-direction: column;
            align-items: center;
            z-index: 1;
            margin-top: 20px;
        }
        .search-bar {
            width: 400px;
            height: 50px;
            border: none;
            padding: 0 20px;
            border-radius: 25px;
            font-size: 18px;
            outline: none;
            margin-top: 20px;
        }
        .search-button {
            height: 50px;
            background-color: orange;
            border: none;
            color: white;
            padding: 0 25px;
            border-radius: 25px;
            font-size: 18px;
            cursor: pointer;
            margin-top: 20px;
            transition: background-color 0.3s, transform 0.3s;
            box-shadow: 0 0 5px orange, 0 0 10px orange, 0 0 20px orange, 0 0 40px orange;
        }
        .search-button:hover {
            background-color: darkorange;
            transform: scale(1.05);
            box-shadow: 0 0 10px orange, 0 0 20px orange, 0 0 30px orange, 0 0 50px orange;
        }
        .logo {
            max-width: 425px;
            margin-bottom: 20px;
        }
        .sidebar {
            position: fixed;
            top: 0;
            left: -200px;
            width: 200px;
            height: 100%;
            background-image: url('https://www.shutterstock.com/image-illustration/orangepurple-gradient-against-stunning-sunset-260nw-1275739732.jpg');
            background-size: cover;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            transition: transform 0.3s;
        }
        .hover-square {
            position: fixed;
            top: 50%;
            left: 0;
            width: 30px;
            height: 30px;
            background-image: url('https://i.imgur.com/uByAmFK_d.webp?maxwidth=760&fidelity=grand');
            background-size: cover;
            cursor: pointer;
            transform: translateY(-50%);
        }
        .hover-square:hover + .sidebar,
        .sidebar:hover {
            transform: translateX(200px);
        }
        .sidebar a {
            color: white;
            text-decoration: none;
            font-size: 18px;
            margin: 15px 0;
            transition: color 0.3s;
        }
        .sidebar a:hover {
            color: darkorange;
        }
        .sidebar a + a {
            border-top: 1px solid white;
            padding-top: 15px;
        }
        .top-bar {
            position: absolute;
            top: calc(100% + 10px);
            right: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 10px;
            border-radius: 5px;
            z-index: 2;
            display: none;
            text-align: center;
        }
        .top-bar span {
            font-size: 20px;
        }
        .loading-img {
            width: 50px;
            animation: rotate 2s linear infinite;
        }
        @keyframes rotate {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }
        .results-container {
            width: 100%;
            flex-grow: 1;
            margin-top: 20px;
            display: none;
            background-color: white;
        }
        .results {
            width: 100%;
            height: 100%;
            border: none;
            display: none;
        }
        .home-page {
            display: block;
        }
        /* Neon falling letters animation */
        .falling-letters {
            position: absolute;
            top: -50px;
            left: 50%;
            font-size: 24px;
            font-family: monospace;
            color: orange;
            text-shadow: 0 0 10px orange, 0 0 20px orange, 0 0 30px orange, 0 0 40px orange, 0 0 50px orange, 0 0 60px orange, 0 0 70px orange;
            animation: fall 5s linear infinite;
            opacity: 0;
        }
        @keyframes fall {
            0% {
                transform: translateY(0);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh);
                opacity: 0;
            }
        }
    </style>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            document.querySelector('.add-tab-button').onclick = addTab;
            var tabs = document.querySelectorAll('.tab');
            tabs.forEach(function(tab) {
                tab.onclick = function() {
                    activateTab(tab);
                };
            });
            customizeBingResults();
            setInterval(createFallingLetter, 600); // Create falling letters every 0.6 seconds
        });

        function openIframe() {
            var newWindow = window.open('about:blank', '_blank');
            newWindow.document.write('<iframe src="https://adfree3kh0.github.io/projects.html" style="width:100%;height:100%;border:none;"></iframe>');
        }

        function openAppsPage() {
            var newWindow = window.open('about:blank', '_blank');
            newWindow.document.write('<iframe src="https://super-duper-fiesta-five.vercel.app/apps.html" style="width:100%;height:100%;border:none;"></iframe>');
        }

        function customizeBingResults() {
            var searchForm = document.getElementById('search-form');
            searchForm.onsubmit = function(event) {
                event.preventDefault();
                var activeTab = document.querySelector('.tab.active');
                var searchQuery = document.querySelector('.search-bar').value;
                var resultsIframe = document.querySelector('.results[data-tab-id="' + activeTab.dataset.tabId + '"]');
                if (!resultsIframe) {
                    resultsIframe = document.createElement('iframe');
                    resultsIframe.className = 'results';
                    resultsIframe.dataset.tabId = activeTab.dataset.tabId;
                    document.querySelector('.results-container').appendChild(resultsIframe);
                }
                resultsIframe.src = 'https://www.bing.com/search?q=' + encodeURIComponent(searchQuery);
                resultsIframe.style.display = 'block';
                hideHomePage();
            };
        }

        function addTab() {
            var tabContainer = document.querySelector('.tab-container');
            var newTabId = 'tab' + (document.querySelectorAll('.tab').length);
            var newTab = document.createElement('div');
            newTab.className = 'tab';
            newTab.dataset.tabId = newTabId;
            newTab.innerHTML = 'New Tab <span class="tab-close" onclick="removeTab(event, this.parentElement)">x</span>';
            tabContainer.insertBefore(newTab, document.querySelector('.add-tab-button'));
            activateTab(newTab);
        }

        function removeTab(event, tab) {
            event.stopPropagation();
            var resultsIframe = document.querySelector('.results[data-tab-id="' + tab.dataset.tabId + '"]');
            if (resultsIframe) resultsIframe.remove();
            tab.remove();
            if (tab.classList.contains('active')) {
                var remainingTabs = document.querySelectorAll('.tab');
                if (remainingTabs.length > 1) {
                    activateTab(remainingTabs[0]);
                } else {
                    showHomePage();
                }
            }
        }

        function activateTab(tab) {
            document.querySelectorAll('.tab').forEach(function(tab) {
                tab.classList.remove('active');
            });
            tab.classList.add('active');
            var tabId = tab.dataset.tabId;
            var iframes = document.querySelectorAll('.results');
            iframes.forEach(function(iframe) {
                iframe.style.display = 'none';
            });
            var activeIframe = document.querySelector('.results[data-tab-id="' + tabId + '"]');
            if (activeIframe) {
                activeIframe.style.display = 'block';
                document.querySelector('.results-container').style.display = 'block';
            } else {
                showHomePage();
            }
        }

        function showHomePage() {
            document.querySelector('.results-container').style.display = 'none';
            document.querySelector('.home-page').style.display = 'block';
        }

        function hideHomePage() {
            document.querySelector('.home-page').style.display = 'none';
            document.querySelector('.results-container').style.display = 'block';
        }

        function createFallingLetter() {
            var characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
            var letter = characters.charAt(Math.floor(Math.random() * characters.length));
            var fallingLetter = document.createElement('span');
            fallingLetter.className = 'falling-letters';
            fallingLetter.textContent = letter;
            fallingLetter.style.left = Math.random() * 100 + 'vw';
            document.body.appendChild(fallingLetter);
            setTimeout(function() {
                fallingLetter.remove();
            }, 5000);
        }
    </script>
</head>
<body>
    <div class="tab-container">
        <div class="tab active" data-tab-id="home">Home</div>
        <button class="add-tab-button">+</button>
    </div>
    <div class="search-container home-page">
        <img src="https://i.imgur.com/kdTzzpB_d.webp?maxwidth=760&fidelity=grand" alt="Logo" class="logo">
        <form id="search-form" method="get" target="_self">
            <input type="text" name="q" class="search-bar" placeholder="Search...">
            <button type="submit" class="search-button">Search</button>
        </form>
        <div class="top-bar"></div>
    </div>
    <div class="results-container"></div>
    <div class="hover-square"></div>
    <div class="sidebar">
        <a href="#" onclick="openIframe()">Games</a>
        <a href="#" onclick="openAppsPage()">Apps</a>
        
    </div>
</body>
</html>
