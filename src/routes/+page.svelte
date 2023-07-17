<script>
    import beatles from "../images/beatles.jpeg"
    import doors from "../images/doors.jpeg"
    import eltonJohn from "../images/eltonJohn.jpeg"
    import pinkFloyd from "../images/pinkFloyd.jpeg"
    import simonGarfunkel from "../images/simon&garfunkel.jpeg"
    import police from "../images/thePolice.jpeg"
    import chuckberry from "../images/chuckberry.jpeg"
    let videos = [
        {
            title: "The Beatles - Eleanor Rigby",
            videoId: "HuS5NuXRb5Y",
            channelName: "The Beatles",
            views: "70M",
            subscriberCount: "7.44M",
            profilePic: beatles
        },
        {
            title: "King Of Pain",
            videoId: "SZlRX03BzeA",
            channelName: "The Police",
            views: "8.9M",
            subscriberCount: "1.66M",
            profilePic: police
        },
        {
            title: "Pink Floyd - Time (2023 Remaster)",
            videoId: "yl-Ms_ek-kE",
            channelName: "Pink Floyd",
            views: "860K",
            subscriberCount: "3.7M",
            profilePic: pinkFloyd
        },
        {
            title: "Elton John - Tiny Dancer",
            videoId: "yYcyacLRPNs",
            channelName: "Elton John",
            views: "166M",
            subscriberCount: "4.07M",
            profilePic: eltonJohn
        },
        {
            title: "Simon & Garfunkel - The Boxer(Audio)",
            videoId: "l3LFML_pxlY",
            channelName: "Simon & Garfunkel",
            views: "78M",
            subscriberCount: "807K",
            profilePic: simonGarfunkel
        },
        {
            title: "Light My Fire (2017 Remaster)",
            videoId: "qoX6AKuYWL8",
            channelName: "The Doors",
            views: "5.5M",
            subscriberCount: "993K",
            profilePic: doors
        },
        {
            title: "Johnny B. Goode",
            videoId: "Uf4rxCB4lys",
            channelName: "Chuck Berry",
            views: "71M",
            subscriberCount: "269K",
            profilePic: chuckberry
        }
    ];

    let currentVideo = videos[0];

    /**
     * @param {{ title: string; videoId: string; channelName: string; views: string; subscriberCount: string; profilePic: string; }} video
     */
    function selectVideo(video) {
        currentVideo = video;
    }
</script>

<div class="video-page">
    <div class="navbar">
        <div class="logo">
            <img
                src="https://www.freepnglogos.com/uploads/youtube-play-red-logo-png-transparent-background-6.png"
                width="200"
                alt="youtube logo"
                style="width: 50px; height: auto;"
            />
            <div class="logo-text">YouTube</div>
        </div>
        <div class="search-bar">
            <input class="search-input" type="text" placeholder="Search" />
            <input class="submit-button" type="submit" value="Search" />
        </div>
    </div>

    <div class="main-video">
        <!-- svelte-ignore a11y-missing-attribute -->
        <iframe
            width="1000"
            height="500"
            src={`https://www.youtube.com/embed/${currentVideo.videoId}`}
            frameborder="0"
            allowfullscreen
        />

        <div class="currentVideo-details">
            <h2 style = "margin: 0; padding: 0;">{currentVideo.title}</h2>
            <h4 style = "margin: 0; padding: 0;">{currentVideo.views} views</h4>
            <div style = "display: flex; flex-direction: row;">
            <img class = "profilePic" src = {currentVideo.profilePic} alt = "{currentVideo.channelName} Profile Picture"/>
            <div style = "display: flex; flex-direction: column;">
            <h3 style = "margin-bottom: 0;">{currentVideo.channelName}</h3>
            <h5 style = "margin-top: 0;">{currentVideo.subscriberCount} Subscribers</h5>
            </div>
            <input class="submit-button subscribeButton" type="submit" value="Subscribe"/>
            </div>
            
        </div>
    </div>
    <div class = "sidebar">
        <h3 style = "margin-top: 0;">Suggested</h3>
        <div class = "video">
            {#each videos.filter(video => video !== currentVideo) as video}
            <!-- svelte-ignore a11y-click-events-have-key-events -->
            <!-- svelte-ignore a11y-no-static-element-interactions -->
            <div class = "sidebar-video" on:click={() => selectVideo(video)}>
            <img
            src={`https://img.youtube.com/vi/${video.videoId}/default.jpg`}
            
            alt={video.title}/>
            <div style = "margin-left: 10px;">
            <h4 style = "margin: 0;padding:0;">{video.title}</h4>
            <h6 style = "margin: 0;padding:0;">{video.channelName}</h6>
            <h5>{video.views} views</h5>
        </div>
        </div>
        {/each}
        </div>
    </div>
</div>


<style>
    .video-page {
        display: grid;
        grid-template-columns: 2fr 1fr;
        gap: 20px;
    }

    .main-video {
        grid-column: 1;
    }

    .sidebar-video {
        cursor: pointer;
        width: 100%;
        display: flex;
        flex-direction: row;
        margin-top: 20px;
        margin-bottom: 20px;
    }

    .navbar {
        display: flex;
        align-items: center;
        padding: 10px;
        background-color: #f1f1f1;
        width: 100%;
    }
    .logo-text {
        font-size: 18px;
        font-weight: bold;
    }
    .logo {
        display: flex;
        align-items: center;
    }
    .search-bar {
        display: flex;
        align-items: center;
        flex-grow: 1;
        margin: 0 10px;
        margin-left: 200px;
        justify-content: center;
    }
    .search-input {
        width: 500px;
        height: 40px;
        padding: 5px 10px;
        border: none;
        border-radius: 50px;
        outline: none;
    }
    .currentVideo-details {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        background-color: #f1f1f1;
        border-radius: 20px;
        margin-left: 10px;
    }
    .subscribeButton {
        height: 30px; 
        width: 100px;
        margin-top: 25px;
        margin-left: 10px;
        border-radius: 15px;
        background-color: red;
        color: white;
    }
    .profilePic {
        margin-left: 2px;
        margin-right: 10px;
        margin-top: 10px;
        width: 60px;
        height: 60px;
        border-radius: 20px;
    }
</style>
