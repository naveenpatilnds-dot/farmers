<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AgriConnect | Farmer-Market Bridge</title>
    <style>
        :root {
            --primary: #2d6a4f;
            --accent: #95d5b2;
            --glass: rgba(255, 255, 255, 0.1);
            --text: #ffffff;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }

        body {
            background: linear-gradient(135deg, #1b4332, #081c15);
            color: var(--text);
            overflow-x: hidden;
            height: 100vh;
        }

        /* Smooth Page Transitions */
        .page {
            display: none;
            padding: 80px 20px;
            animation: fadeIn 0.8s ease-out;
            min-height: 100vh;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Navigation Logic (No-JS Toggle) */
        #home-toggle:checked ~ #home,
        #market-toggle:checked ~ #market,
        #chat-toggle:checked ~ #chat { display: block; }

        input[type="radio"] { display: none; }

        nav {
            position: fixed;
            top: 0; width: 100%;
            background: rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            display: flex;
            justify-content: center;
            padding: 15px;
            z-index: 1000;
            border-bottom: 1px solid var(--glass);
        }

        nav label {
            margin: 0 20px;
            cursor: pointer;
            font-weight: 600;
            transition: 0.3s;
            opacity: 0.7;
        }

        nav label:hover { opacity: 1; color: var(--accent); }

        /* Component Styles */
        .hero {
            text-align: center;
            max-width: 800px;
            margin: 100px auto;
        }

        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            max-width: 1200px;
            margin: auto;
        }

        .card {
            background: var(--glass);
            padding: 20px;
            border-radius: 20px;
            border: 1px solid rgba(255,255,255,0.1);
            backdrop-filter: blur(5px);
            transition: transform 0.3s ease;
        }

        .card:hover { transform: scale(1.05); border-color: var(--accent); }

        /* Chat System Simulation */
        .chat-box {
            max-width: 600px;
            margin: auto;
            background: rgba(0,0,0,0.5);
            border-radius: 20px;
            height: 400px;
            display: flex;
            flex-direction: column;
            padding: 20px;
        }

        .message {
            margin-bottom: 15px;
            padding: 10px 15px;
            border-radius: 15px;
            max-width: 80%;
        }

        .farmer { background: var(--primary); align-self: flex-start; }
        .market { background: #457b9d; align-self: flex-end; }

        .btn {
            background: var(--accent);
            color: #081c15;
            padding: 12px 30px;
            border-radius: 30px;
            text-decoration: none;
            display: inline-block;
            margin-top: 20px;
            font-weight: bold;
            transition: 0.3s;
        }

        .btn:hover { box-shadow: 0 0 20px var(--accent); }
    </style>
</head>
<body>

    <input type="radio" name="nav" id="home-toggle" checked>
    <input type="radio" name="nav" id="market-toggle">
    <input type="radio" name="nav" id="chat-toggle">

    <nav>
        <label for="home-toggle">Home</label>
        <label for="market-toggle">Marketplace</label>
        <label for="chat-toggle">Direct Message</label>
    </nav>

    <section class="page" id="home">
        <div class="hero">
            <h1>Empowering Farmers via Direct Trade</h1>
            <p style="margin-top: 20px; opacity: 0.8;">Eliminate the middleman. Connect directly with bulk buyers and local markets in real-time with hyper-local data.</p>
            <label for="market-toggle" class="btn">Explore Produce</label>
        </div>
    </section>

    <section class="page" id="market">
        <h2 style="text-align: center; margin-bottom: 40px;">Live Market Listings</h2>
        <div class="card-grid">
            <div class="card">
                <h3>Organic Wheat</h3>
                <p>Qty: 500kg</p>
                <p>Location: Punjab Farms</p>
                <label for="chat-toggle" class="btn" style="padding: 5px 15px; font-size: 0.8em;">Contact Farmer</label>
            </div>
            <div class="card">
                <h3>Fresh Tomatoes</h3>
                <p>Qty: 120kg</p>
                <p>Location: Karnataka Hub</p>
                <label for="chat-toggle" class="btn" style="padding: 5px 15px; font-size: 0.8em;">Contact Farmer</label>
            </div>
            <div class="card">
                <h3>Golden Corn</h3>
                <p>Qty: 1000kg</p>
                <p>Location: Ohio Valley</p>
                <label for="chat-toggle" class="btn" style="padding: 5px 15px; font-size: 0.8em;">Contact Farmer</label>
            </div>
        </div>
    </section>

    <section class="page" id="chat">
        <h2 style="text-align: center; margin-bottom: 40px;">Direct Negotiation</h2>
        <div class="chat-box">
            <div class="message farmer">Hello, I have 500kg of organic wheat ready for transport. Are you interested?</div>
            <div class="message market">Yes, what is your best price per kg for bulk purchase?</div>
            <div class="message farmer">I can offer $2.50/kg if you handle the pickup.</div>
            <div style="margin-top: auto; display: flex; gap: 10px;">
                <input type="text" placeholder="Type your offer..." style="flex:1; padding: 10px; border-radius: 10px; border: none;">
                <button class="btn" style="margin:0; padding: 10px 20px;">Send</button>
            </div>
        </div>
    </section>

</body>
</html>
