<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Mobile AR Dental Scanner</title>
    
    <!-- Load MediaPipe Face Mesh Libraries -->
    <script src="https://jsdelivr.net" crossorigin="anonymous"></script>
    <script src="https://jsdelivr.net" crossorigin="anonymous"></script>

    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background-color: #0d1117;
            color: #c9d1d9;
            overflow-x: hidden;
        }
        header {
            background-color: #161b22;
            padding: 12px;
            text-align: center;
            border-bottom: 1px solid #30363d;
        }
        h1 { margin: 0; font-size: 1.1rem; color: #58a6ff; }
        
        .container {
            display: flex;
            flex-direction: column;
            padding: 10px;
            gap: 12px;
            box-sizing: border-box;
        }

        .ar-view-box {
            position: relative;
            width: 100%;
            background: #000;
            border-radius: 12px;
            border: 1px solid #30363d;
            overflow: hidden;
            aspect-ratio: 4/3;
        }
        #webcam {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transform: scaleX(-1);
        }
        #output_canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            transform: scaleX(-1);
            pointer-events: none;
        }

        .data-panel {
            background-color: #161b22;
            border: 1px solid #30363d;
            border-radius: 12px;
            padding: 15px;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        .panel-title {
            font-size: 1rem;
            font-weight: bold;
            color: #58a6ff;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .data-card {
            background: #21262d;
            padding: 10px;
            border-radius: 8px;
            border-left: 3px solid #30363d;
        }
        .data-card.active-gene { border-left-color: #ff7b72; }
        .data-card.active-protein { border-left-color: #7ee787; }
        .label { font-size: 0.75rem; text-transform: uppercase; color: #8b949e; font-weight: bold; }
        .value { font-size: 0.9rem; margin-top: 2px; color: #f0f6fc; line-height: 1.3; }
        
        .status-tag {
            padding: 2px 6px;
            border-radius: 4px;
            font-size: 0.75rem;
            font-weight: bold;
            background: #21262d;
            color: #8b949e;
        }
        .status-tag.tracking { background: rgba(56, 139, 253, 0.2); color: #58a6ff; }
    </style>
</head>
<body>

    <header>
        <h1>Dental AR: Genome-to-Proteome</h1>
    </header>

    <div class="container">
        <div class="ar-view-box">
            <!-- Added user facing camera configurations for mobile screens -->
            <video id="webcam" autoplay playsinline muted></video>
            <canvas id="output_canvas"></canvas>
        </div>

        <div class="data-panel">
            <div class="panel-title">
                <span>Omics Telemetry</span>
                <span id="status" class="status-tag">Starting...</span>
            </div>
            
            <div class="data-card">
                <div class="label">Zone</div>
                <div id="zone-val" class="value">Awaiting Tracking...</div>
            </div>
            
            <div class="data-card active-gene">
                <div class="label">DNA Genes</div>
                <div id="gene-val" class="value">—</div>
            </div>
            
            <div class="data-card active-protein">
                <div class="label">Proteome Matrix</div>
                <div id="proteome-val" class="value">—</div>
            </div>
        </div>
    </div>

    <script>
        const videoElement = document.getElementById('webcam');
        const canvasElement = document.getElementById('output_canvas');
        const canvasCtx = canvasElement.getContext('2d');
        const statusTag = document.getElementById('status');

        const zoneVal = document.getElementById('zone-val');
        const geneVal = document.getElementById('gene-val');
        const proteomeVal = document.getElementById('proteome-val');

        function updateOmicsData(isMouthOpen) {
            if (!isMouthOpen) {
                zoneVal.innerText = "Mouth Closed";
                geneVal.innerText = "Basal Control Expression";
                proteomeVal.innerText = "Salivary Enzymes Active";
            } else {
                zoneVal.innerText = "Maxillary Enamel Arch";
                geneVal.innerText = "AMELX, ENAM, PAX9";
                proteomeVal.innerText = "Amelogenin Matrix (90%)";
            }
        }

        function onResults(results) {
            if (canvasElement.width !== videoElement.videoWidth) {
                canvasElement.width = videoElement.videoWidth;
                canvasElement.height = videoElement.videoHeight;
            }

            canvasCtx.save();
            canvasCtx.clearRect(0, 0, canvasElement.width, canvasElement.height);

            if (results.multiFaceLandmarks && results.multiFaceLandmarks.length > 0) {
                statusTag.innerText = "SCANNING";
                statusTag.className = "status-tag tracking";
                
                const landmarks = results.multiFaceLandmarks[0];
                const topLip = landmarks[0];
                const bottomLip = landmarks[17];
                
                const distance = Math.sqrt(Math.pow(topLip.x - bottomLip.x, 2) + Math.pow(topLip.y - bottomLip.y, 2));
                const isMouthOpen = distance > 0.05; 
                updateOmicsData(isMouthOpen);

                // Quick lip boundary draw loop
                const lipIndices =;
                canvasCtx.beginPath();
                lipIndices.forEach((idx, i) => {
                    const pt = landmarks[idx];
                    if (i === 0) canvasCtx.moveTo(pt.x * canvasElement.width, pt.y * canvasElement.height);
                    else canvasCtx.lineTo(pt.x * canvasElement.width, pt.y * canvasElement.height);
                });
                canvasCtx.closePath();

                if (isMouthOpen) {
                    canvasCtx.strokeStyle = '#7ee787';
                    canvasCtx.lineWidth = 3;
                    canvasCtx.fillStyle = 'rgba(126, 231, 135, 0.15)';
                    canvasCtx.fill();
                } else {
                    canvasCtx.strokeStyle = '#58a6ff';
                    canvasCtx.lineWidth = 2;
                }
                canvasCtx.stroke();
            } else {
                statusTag.innerText = "NO FACE";
                statusTag.className = "status-tag";
                updateOmicsData(false);
            }
            canvasCtx.restore();
        }

        const faceMesh = new FaceMesh({
            locateFile: (file) => `https://jsdelivr.net{file}`
        });

        faceMesh.setOptions({
            maxNumFaces: 1,
            refineLandmarks: true,
            minDetectionConfidence: 0.5,
            minTrackingConfidence: 0.5
        });
        faceMesh.onResults(onResults);

        // Mobile optimized camera constraints forcing the front camera
        const camera = new Camera(videoElement, {
            onFrame: async () => {
                await faceMesh.send({ image: videoElement });
            },
            width: 640,
            height: 480,
            facingMode: 'user'
        });
        
        camera.start().catch(err => {
            statusTag.innerText = "ERR";
            alert("Please allow camera access and use HTTPS link.");
        });
    </script>
</body>
</html>
