<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>san valentin</title>
    <style>
        body {
            background-color: #FEA8C5;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            font-family: Arial, sans-serif;
            text-align: center;
        }
        h1 {
            color: #d46a85;
            font-size: 2.5rem;
            margin-bottom: 20px;
        }
        .gif-container {
            margin: 20px 0;
        }
        .gif-container img {
            width: 150px;
            height: auto;
        }
        .btn {
            font-size: 1.5rem;
            padding: 10px 20px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 10px;
        }
        .yes-btn {
            background-color: green;
            color: white;
            transition: font-size 0.3s ease;
        }
        .no-btn {
            background-color: orangered;
            color: white;
        }
        .hidden {
            display: none;
        }
        .full-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background-color: #F1BFF6;
        }
        .full-screen img {
            width: 50%;
            height: auto;
        }
        .expanded-yes {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            font-size: 4rem;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .video-container {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: rgba(0, 0, 0, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
        }
        video {
            width: 80%;
            max-height: 80vh;
        }
    </style>
</head>
<body>
    <h1>Quieres ser mi San Valentin?</h1>
    <div class="gif-container">
        <img src="valentine.gif" alt="Happy Bear">
    </div>
    <button class="btn yes-btn">Si</button>
    <button class="btn no-btn">No</button>
    <script>
        const yesButton = document.querySelector('.yes-btn');
        const noButton = document.querySelector('.no-btn');
        const question = document.querySelector('h1');
        const gifContainer = document.querySelector('.gif-container');
        let noClickCount = 0;
        const noTexts = [
            "Estás realmente segura?",
            "Piensalo un poco más... ",
            "que grosera, una oportunidad mas",
            "ok, chimba, diga que si",
            "mmm ya, todavia no?",
            "deme a shooky y arturo entonces :/",
            "enserio 😢"
        ];
        noButton.addEventListener('click', () => {
            if (noClickCount < noTexts.length) {
                noButton.textContent = noTexts[noClickCount];
                yesButton.style.fontSize = `${1.5 + noClickCount * 5}rem`;
                noClickCount++;
            } else {
                yesButton.classList.add('expanded-yes');
                yesButton.textContent = "SII";
                question.classList.add('hidden');
                gifContainer.classList.add('hidden');
                noButton.classList.add('hidden');
            }
        });
        yesButton.addEventListener('click', () => {
            document.body.innerHTML = `
                <div class="full-screen">
                    <img src="dog.gif" alt="Happy Dog">
                     <img src="so.png" alt="Happy Dog">
                    

                    <button class="btn" id="play-video">Reproducir Video</button>
                </div>
                <div class="video-container" id="video-container">
                    <video controls>
                        <source src="vavi.mp4" type="video/mp4">
                        Tu navegador no soporta el video.
                    </video>
                </div>
            `;
            
            document.getElementById('play-video').addEventListener('click', () => {
                document.querySelector('.full-screen').style.display = 'none';
                document.getElementById('video-container').style.display = 'flex';
            });
        });
    </script>
</body>
</html>
