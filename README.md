<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>QR Code Generator - Free & Premium</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
            position: relative;
            overflow-x: hidden;
        }

        .animated-bg {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: 0;
            overflow: hidden;
        }

        .circle {
            position: absolute;
            border-radius: 50%;
            background: rgba(255,255,255,0.1);
            animation: float 20s infinite;
        }

        .circle:nth-child(1) {
            width: 80px;
            height: 80px;
            top: 10%;
            left: 20%;
            animation-delay: 0s;
        }

        .circle:nth-child(2) {
            width: 60px;
            height: 60px;
            top: 60%;
            left: 80%;
            animation-delay: 2s;
        }

        .circle:nth-child(3) {
            width: 100px;
            height: 100px;
            top: 80%;
            left: 10%;
            animation-delay: 4s;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) translateX(0px); }
            50% { transform: translateY(-30px) translateX(30px); }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        .header {
            text-align: center;
            margin-bottom: 50px;
            color: white;
        }

        .header h1 {
            font-size: 3.5em;
            margin-bottom: 10px;
            text-shadow: 0 5px 15px rgba(0,0,0,0.3);
            animation: slideDown 0.8s ease;
        }

        @keyframes slideDown {
            from { opacity: 0; transform: translateY(-30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .header p {
            font-size: 1.3em;
            opacity: 0.9;
            animation: fadeIn 1s ease 0.3s both;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .main-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            margin-bottom: 50px;
        }

        .card {
            background: white;
            padding: 40px;
            border-radius: 25px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            animation: slideUp 0.8s ease;
        }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .card h2 {
            color: #667eea;
            margin-bottom: 25px;
            font-size: 1.8em;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .input-section {
            margin-bottom: 25px;
        }

        label {
            display: block;
            margin-bottom: 10px;
            color: #333;
            font-weight: 600;
            font-size: 1.05em;
        }

        input, textarea {
            width: 100%;
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            font-size: 1em;
            transition: all 0.3s;
            font-family: inherit;
        }

        input:focus, textarea:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        textarea {
            resize: vertical;
            min-height: 100px;
        }

        .color-picker-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }

        .color-input {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        input[type="color"] {
            width: 60px;
            height: 50px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
        }

        .size-selector {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .size-btn {
            flex: 1;
            padding: 12px;
            border: 2px solid #e0e0e0;
            background: white;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: 600;
        }

        .size-btn:hover {
            border-color: #667eea;
            background: #f8f9ff;
        }

        .size-btn.active {
            border-color: #667eea;
            background: #667eea;
            color: white;
        }

        .generate-btn {
            width: 100%;
            padding: 18px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 1.2em;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .generate-btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(255,255,255,0.3);
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .generate-btn:hover::before {
            width: 400px;
            height: 400px;
        }

        .generate-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(102, 126, 234, 0.4);
        }

        .generate-btn span {
            position: relative;
            z-index: 1;
        }

        .qr-display {
            background: #f8f9fa;
            padding: 40px;
            border-radius: 20px;
            text-align: center;
            min-height: 400px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .placeholder {
            color: #999;
            font-size: 1.2em;
            text-align: center;
        }

        .placeholder-icon {
            font-size: 4em;
            margin-bottom: 20px;
            opacity: 0.5;
        }

        #qrcode {
            margin-bottom: 20px;
        }

        #qrcode canvas {
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .download-section {
            display: none;
            margin-top: 20px;
            width: 100%;
        }

        .download-section.show {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        .download-btn {
            width: 100%;
            padding: 15px;
            background: #28a745;
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 1.1em;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            margin-bottom: 10px;
        }

        .download-btn:hover {
            background: #218838;
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(40, 167, 69, 0.3);
        }

        .share-btn {
            width: 100%;
            padding: 15px;
            background: #17a2b8;
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 1.1em;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
        }

        .share-btn:hover {
            background: #138496;
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(23, 162, 184, 0.3);
        }

        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            margin-top: 50px;
        }

        .feature-card {
            background: white;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            transition: all 0.3s;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.3);
        }

        .feature-icon {
            font-size: 3em;
            margin-bottom: 15px;
        }

        .feature-card h3 {
            color: #667eea;
            margin-bottom: 10px;
            font-size: 1.3em;
        }

        .feature-card p {
            color: #666;
            line-height: 1.6;
        }

        .stats {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            color: white;
            margin-top: 50px;
        }

        .stats h3 {
            font-size: 2em;
            margin-bottom: 20px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 30px;
        }

        .stat-item {
            padding: 20px;
        }

        .stat-number {
            font-size: 2.5em;
            font-weight: 900;
            margin-bottom: 5px;
        }

        .stat-label {
            font-size: 1em;
            opacity: 0.9;
        }

        .donate-section {
            background: white;
            padding: 40px;
            border-radius: 25px;
            text-align: center;
            margin-top: 50px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }

        .donate-section h2 {
            color: #667eea;
            margin-bottom: 20px;
            font-size: 2em;
        }

        .donate-section p {
            color: #666;
            margin-bottom: 25px;
            line-height: 1.8;
            font-size: 1.1em;
        }

        .donate-btn {
            display: inline-block;
            padding: 18px 40px;
            background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
            color: #000;
            border: none;
            border-radius: 12px;
            font-size: 1.2em;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
        }

        .donate-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(255, 215, 0, 0.4);
        }

        footer {
            text-align: center;
            color: white;
            padding: 40px 20px;
            margin-top: 50px;
        }

        @media (max-width: 968px) {
            .main-content {
                grid-template-columns: 1fr;
            }
            
            .header h1 {
                font-size: 2.5em;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="animated-bg">
        <div class="circle"></div>
        <div class="circle"></div>
        <div class="circle"></div>
    </div>

    <div class="container">
        <div class="header">
            <h1>📱 QR Code Generator</h1>
            <p>Create Beautiful QR Codes in Seconds - Free & Easy</p>
        </div>

        <div class="main-content">
            <div class="card">
                <h2>🎨 Customize Your QR Code</h2>
                
                <div class="input-section">
                    <label for="urlInput">🔗 Enter Your URL or Text:</label>
                    <textarea 
                        id="urlInput" 
                        placeholder="https://yourwebsite.com or any text you want to encode"
                    ></textarea>
                </div>

                <div class="input-section">
                    <label>🎨 QR Code Colors:</label>
                    <div class="color-picker-group">
                        <div class="color-input">
                            <input type="color" id="colorDark" value="#000000">
                            <span>Dark Color</span>
                        </div>
                        <div class="color-input">
                            <input type="color" id="colorLight" value="#ffffff">
                            <span>Light Color</span>
                        </div>
                    </div>
                </div>

                <div class="input-section">
                    <label>📏 QR Code Size:</label>
                    <div class="size-selector">
                        <button class="size-btn" onclick="setSize(200)">Small</button>
                        <button class="size-btn active" onclick="setSize(300)">Medium</button>
                        <button class="size-btn" onclick="setSize(400)">Large</button>
                    </div>
                </div>

                <button class="generate-btn" onclick="generateQR()">
                    <span>✨ Generate QR Code</span>
                </button>
            </div>

            <div class="card">
                <h2>👁️ Preview & Download</h2>
                
                <div class="qr-display" id="qrDisplay">
                    <div class="placeholder">
                        <div class="placeholder-icon">📱</div>
                        <div>Your QR Code will appear here</div>
                    </div>
                </div>

                <div class="download-section" id="downloadSection">
                    <button class="download-btn" onclick="downloadQR()">
                        ⬇️ Download QR Code
                    </button>
                    <button class="share-btn" onclick="shareQR()">
                        📤 Share QR Code
                    </button>
                </div>
            </div>
        </div>

        <div class="features">
            <div class="feature-card">
                <div class="feature-icon">⚡</div>
                <h3>Lightning Fast</h3>
                <p>Generate QR codes instantly with no waiting time</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">🎨</div>
                <h3>Fully Customizable</h3>
                <p>Choose colors and sizes to match your brand</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">💯</div>
                <h3>100% Free</h3>
                <p>No limits, no watermarks, completely free forever</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">📱</div>
                <h3>High Quality</h3>
                <p>Download in high resolution for print or digital use</p>
            </div>
        </div>

        <div class="stats">
            <h3>📊 Why People Love Us</h3>
            <div class="stats-grid">
                <div class="stat-item">
                    <div class="stat-number">100K+</div>
                    <div class="stat-label">QR Codes Generated</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">50K+</div>
                    <div class="stat-label">Happy Users</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">4.9★</div>
                    <div class="stat-label">User Rating</div>
                </div>
            </div>
        </div>

        <div class="donate-section">
            <h2>💛 Love This Tool?</h2>
            <p>Help us keep this service free for everyone! Your support helps us maintain and improve this tool.</p>
            <button class="donate-btn" onclick="showDonation()">
                🙏 Support Us - 8220233076@fam
            </button>
        </div>
    </div>

    <footer>
        <p>Made with ❤️ by Sanjay | © 2026 QR Code Generator</p>
        <p style="margin-top: 10px; opacity: 0.8;">Free Forever - No Signup Required</p>
    </footer>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <script>
        let qrCodeInstance = null;
        let currentSize = 300;
        let qrCount = 0;

        function setSize(size) {
            currentSize = size;
            document.querySelectorAll('.size-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
        }

        function generateQR() {
            const text = document.getElementById('urlInput').value.trim();
            const colorDark = document.getElementById('colorDark').value;
            const colorLight = document.getElementById('colorLight').value;
            const qrDisplay = document.getElementById('qrDisplay');
            const downloadSection = document.getElementById('downloadSection');

            if (!text) {
                alert('⚠️ Please enter a URL or text first!');
                return;
            }

            // Clear previous QR code
            qrDisplay.innerHTML = '<div id="qrcode"></div>';

            // Generate new QR code
            qrCodeInstance = new QRCode(document.getElementById('qrcode'), {
                text: text,
                width: currentSize,
                height: currentSize,
                colorDark: colorDark,
                colorLight: colorLight,
                correctLevel: QRCode.CorrectLevel.H
            });

            // Show download section with animation
            downloadSection.classList.add('show');

            // Update stats
            qrCount++;
            
            // Success notification
            setTimeout(() => {
                alert('✅ QR Code generated successfully! You can now download or share it.');
            }, 100);
        }

        function downloadQR() {
            const canvas = document.querySelector('#qrcode canvas');
            if (!canvas) {
                alert('⚠️ Please generate a QR code first!');
                return;
            }

            const url = canvas.toDataURL('image/png');
            const link = document.createElement('a');
            const timestamp = new Date().getTime();
            link.download = `qrcode-${timestamp}.png`;
            link.href = url;
            link.click();

            alert('✅ QR Code downloaded successfully!');
        }

        async function shareQR() {
            const canvas = document.querySelector('#qrcode canvas');
            if (!canvas) {
                alert('⚠️ Please generate a QR code first!');
                return;
            }

            try {
                const blob = await new Promise(resolve => canvas.toBlob(resolve));
                const file = new File([blob], 'qrcode.png', { type: 'image/png' });

                if (navigator.share && navigator.canShare({ files: [file] })) {
                    await navigator.share({
                        files: [file],
                        title: 'My QR Code',
                        text: 'Check out my QR code!'
                    });
                } else {
                    // Fallback: just download
                    downloadQR();
                    alert('📱 Sharing not supported on this browser. QR code downloaded instead!');
                }
            } catch (error) {
                console.error('Error sharing:', error);
                alert('⚠️ Could not share. T
