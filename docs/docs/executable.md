<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quantum Router 3D Dashboard</title>
    <style>
        :root {
            --primary: #6200ee;
            --secondary: #03dac6;
            --dark: #121212;
            --light: #ffffff;
        }
        
        body {
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--dark);
            color: var(--light);
            overflow-x: hidden;
            perspective: 1000px;
        }
        
        .dashboard {
            display: grid;
            grid-template-columns: 250px 1fr;
            min-height: 100vh;
        }
        
        .sidebar {
            background: rgba(18, 18, 18, 0.8);
            backdrop-filter: blur(10px);
            padding: 2rem;
            border-right: 1px solid rgba(255, 255, 255, 0.1);
            transform-style: preserve-3d;
            transform: translateZ(-50px);
        }
        
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 2rem;
            color: var(--secondary);
            text-align: center;
        }
        
        .nav-item {
            padding: 1rem;
            margin: 0.5rem 0;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
        }
        
        .nav-item:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateX(10px);
        }
        
        .nav-item i {
            margin-right: 1rem;
        }
        
        .main-content {
            padding: 2rem;
            transform-style: preserve-3d;
        }
        
        .card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 16px;
            padding: 1.5rem;
            margin-bottom: 2rem;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            transform-style: preserve-3d;
        }
        
        .card:hover {
            transform: translateY(-5px) rotateX(5deg);
            box-shadow: 0 12px 40px rgba(0, 0, 0, 0.4);
        }
        
        .card-header {
            font-size: 1.2rem;
            margin-bottom: 1rem;
            color: var(--secondary);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .status-indicator {
            display: inline-block;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #4caf50;
            margin-right: 0.5rem;
        }
        
        .network-visualization {
            width: 100%;
            height: 300px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 8px;
            position: relative;
            overflow: hidden;
        }
        
        .device-node {
            position: absolute;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: var(--primary);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-weight: bold;
            box-shadow: 0 0 20px rgba(98, 0, 238, 0.5);
            transform-style: preserve-3d;
            animation: float 3s infinite ease-in-out;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0) rotateY(0); }
            50% { transform: translateY(-10px) rotateY(10deg); }
        }
        
        .speed-test {
            display: flex;
            justify-content: space-around;
            text-align: center;
        }
        
        .speed-meter {
            width: 150px;
            height: 150px;
            position: relative;
        }
        
        .speed-value {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 1.5rem;
            font-weight: bold;
        }
        
        .btn {
            padding: 0.8rem 1.5rem;
            border: none;
            border-radius: 8px;
            background: var(--primary);
            color: white;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .btn:hover {
            background: var(--secondary);
            transform: translateY(-2px);
        }
        
        .btn-3d {
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transform-style: preserve-3d;
        }
        
        .btn-3d:active {
            transform: translateY(2px);
        }
    </style>
</head>
<body>
    <div class="dashboard">
        <div class="sidebar">
            <div class="logo">QUANTUM ROUTER</div>
            <div class="nav-item">
                <i>📊</i> Dashboard
            </div>
            <div class="nav-item">
                <i>📶</i> Network Status
            </div>
            <div class="nav-item">
                <i>🔒</i> Security
            </div>
            <div class="nav-item">
                <i>🔄</i> Firmware Update
            </div>
            <div class="nav-item">
                <i>⚙️</i> Advanced Settings
            </div>
            <div class="nav-item">
                <i>🛡️</i> Parental Controls
            </div>
            <div class="nav-item">
                <i>📱</i> Connected Devices
            </div>
        </div>
        
        <div class="main-content">
            <h1>Dashboard <span class="status-indicator"></span></h1>
            
            <div class="card">
                <div class="card-header">
                    <span>Network Visualization</span>
                </div>
                <div class="network-visualization">
                    <div class="device-node" style="top: 50%; left: 50%; transform: translate(-50%, -50%);">ROUTER</div>
                    <div class="device-node" style="top: 30%; left: 30%;">Laptop</div>
                    <div class="device-node" style="top: 70%; left: 20%;">Phone</div>
                    <div class="device-node" style="top: 20%; left: 70%;">TV</div>
                    <div class="device-node" style="top: 80%; left: 75%;">Tablet</div>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <span>Connection Status</span>
                </div>
                <div class="speed-test">
                    <div class="speed-meter">
                        <svg width="150" height="150" viewBox="0 0 150 150">
                            <circle cx="75" cy="75" r="60" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="10"/>
                            <circle cx="75" cy="75" r="60" fill="none" stroke="var(--secondary)" stroke-width="10" 
                                    stroke-dasharray="377" stroke-dashoffset="113" stroke-linecap="round"
                                    transform="rotate(-90 75 75)"/>
                        </svg>
                        <div class="speed-value">300 Mbps</div>
                        <div style="margin-top: 10px;">Download</div>
                    </div>
                    <div class="speed-meter">
                        <svg width="150" height="150" viewBox="0 0 150 150">
                            <circle cx="75" cy="75" r="60" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="10"/>
                            <circle cx="75" cy="75" r="60" fill="none" stroke="var(--primary)" stroke-width="10" 
                                    stroke-dasharray="377" stroke-dashoffset="226" stroke-linecap="round"
                                    transform="rotate(-90 75 75)"/>
                        </svg>
                        <div class="speed-value">150 Mbps</div>
                        <div style="margin-top: 10px;">Upload</div>
                    </div>
                    <div class="speed-meter">
                        <svg width="150" height="150" viewBox="0 0 150 150">
                            <circle cx="75" cy="75" r="60" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="10"/>
                            <circle cx="75" cy="75" r="60" fill="none" stroke="#ff9800" stroke-width="10" 
                                    stroke-dasharray="377" stroke-dashoffset="30" stroke-linecap="round"
                                    transform="rotate(-90 75 75)"/>
                        </svg>
                        <div class="speed-value">12 ms</div>
                        <div style="margin-top: 10px;">Ping</div>
                    </div>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <span>Quick Actions</span>
                </div>
                <div style="display: flex; gap: 1rem;">
                    <button class="btn btn-3d">Restart Router</button>
                    <button class="btn btn-3d">Run Speed Test</button>
                    <button class="btn btn-3d">Block Device</button>
                    <button class="btn btn-3d">Guest Network</button>
                </div>
            </div>
        </div>
    </div>
    
    <script>
        // Simple animation for device nodes
        document.querySelectorAll('.device-node').forEach((node, index) => {
            if(index > 0) {
                const delay = index * 0.2;
                node.style.animationDelay = `${delay}s`;
                
                // Create connection lines (would be better with canvas/SVG)
                const router = document.querySelector('.device-node:first-child');
                const line = document.createElement('div');
                line.style.position = 'absolute';
                line.style.backgroundColor = 'rgba(3, 218, 198, 0.3)';
                line.style.height = '2px';
                line.style.transformOrigin = '0 0';
                line.style.zIndex = '-1';
                
                const routerRect = router.getBoundingClientRect();
                const nodeRect = node.getBoundingClientRect();
                const networkViz = document.querySelector('.network-visualization');
                const vizRect = networkViz.getBoundingClientRect();
                
                const routerX = routerRect.left + routerRect.width/2 - vizRect.left;
                const routerY = routerRect.top + routerRect.height/2 - vizRect.top;
                const nodeX = nodeRect.left + nodeRect.width/2 - vizRect.left;
                const nodeY = nodeRect.top + nodeRect.height/2 - vizRect.top;
                
                const length = Math.sqrt(Math.pow(nodeX - routerX, 2) + Math.pow(nodeY - routerY, 2));
                const angle = Math.atan2(nodeY - routerY, nodeX - routerX) * 180 / Math.PI;
                
                line.style.width = `${length}px`;
                line.style.left = `${routerX}px`;
                line.style.top = `${routerY}px`;
                line.style.transform = `rotate(${angle}deg)`;
                
                networkViz.appendChild(line);
            }
        });
    </script>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quantum Router 3D Dashboard</title>
    <style>
        :root {
            --primary: #6200ee;
            --secondary: #03dac6;
            --dark: #121212;
            --light: #ffffff;
        }
        
        body {
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--dark);
            color: var(--light);
            overflow-x: hidden;
            perspective: 1000px;
        }
        
        .dashboard {
            display: grid;
            grid-template-columns: 250px 1fr;
            min-height: 100vh;
        }
        
        .sidebar {
            background: rgba(18, 18, 18, 0.8);
            backdrop-filter: blur(10px);
            padding: 2rem;
            border-right: 1px solid rgba(255, 255, 255, 0.1);
            transform-style: preserve-3d;
            transform: translateZ(-50px);
        }
        
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 2rem;
            color: var(--secondary);
            text-align: center;
        }
        
        .nav-item {
            padding: 1rem;
            margin: 0.5rem 0;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
        }
        
        .nav-item:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateX(10px);
        }
        
        .nav-item i {
            margin-right: 1rem;
        }
        
        .main-content {
            padding: 2rem;
            transform-style: preserve-3d;
        }
        
        .card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 16px;
            padding: 1.5rem;
            margin-bottom: 2rem;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            transform-style: preserve-3d;
        }
        
        .card:hover {
            transform: translateY(-5px) rotateX(5deg);
            box-shadow: 0 12px 40px rgba(0, 0, 0, 0.4);
        }
        
        .card-header {
            font-size: 1.2rem;
            margin-bottom: 1rem;
            color: var(--secondary);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .status-indicator {
            display: inline-block;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #4caf50;
            margin-right: 0.5rem;
        }
        
        .network-visualization {
            width: 100%;
            height: 300px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 8px;
            position: relative;
            overflow: hidden;
        }
        
        .device-node {
            position: absolute;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: var(--primary);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-weight: bold;
            box-shadow: 0 0 20px rgba(98, 0, 238, 0.5);
            transform-style: preserve-3d;
            animation: float 3s infinite ease-in-out;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0) rotateY(0); }
            50% { transform: translateY(-10px) rotateY(10deg); }
        }
        
        .speed-test {
            display: flex;
            justify-content: space-around;
            text-align: center;
        }
        
        .speed-meter {
            width: 150px;
            height: 150px;
            position: relative;
        }
        
        .speed-value {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 1.5rem;
            font-weight: bold;
        }
        
        .btn {
            padding: 0.8rem 1.5rem;
            border: none;
            border-radius: 8px;
            background: var(--primary);
            color: white;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .btn:hover {
            background: var(--secondary);
            transform: translateY(-2px);
        }
        
        .btn-3d {
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transform-style: preserve-3d;
        }
        
        .btn-3d:active {
            transform: translateY(2px);
        }
    </style>
</head>
<body>
    <div class="dashboard">
        <div class="sidebar">
            <div class="logo">QUANTUM ROUTER</div>
            <div class="nav-item">
                <i>📊</i> Dashboard
            </div>
            <div class="nav-item">
                <i>📶</i> Network Status
            </div>
            <div class="nav-item">
                <i>🔒</i> Security
            </div>
            <div class="nav-item">
                <i>🔄</i> Firmware Update
            </div>
            <div class="nav-item">
                <i>⚙️</i> Advanced Settings
            </div>
            <div class="nav-item">
                <i>🛡️</i> Parental Controls
            </div>
            <div class="nav-item">
                <i>📱</i> Connected Devices
            </div>
        </div>
        
        <div class="main-content">
            <h1>Dashboard <span class="status-indicator"></span></h1>
            
            <div class="card">
                <div class="card-header">
                    <span>Network Visualization</span>
                </div>
                <div class="network-visualization">
                    <div class="device-node" style="top: 50%; left: 50%; transform: translate(-50%, -50%);">ROUTER</div>
                    <div class="device-node" style="top: 30%; left: 30%;">Laptop</div>
                    <div class="device-node" style="top: 70%; left: 20%;">Phone</div>
                    <div class="device-node" style="top: 20%; left: 70%;">TV</div>
                    <div class="device-node" style="top: 80%; left: 75%;">Tablet</div>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <span>Connection Status</span>
                </div>
                <div class="speed-test">
                    <div class="speed-meter">
                        <svg width="150" height="150" viewBox="0 0 150 150">
                            <circle cx="75" cy="75" r="60" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="10"/>
                            <circle cx="75" cy="75" r="60" fill="none" stroke="var(--secondary)" stroke-width="10" 
                                    stroke-dasharray="377" stroke-dashoffset="113" stroke-linecap="round"
                                    transform="rotate(-90 75 75)"/>
                        </svg>
                        <div class="speed-value">300 Mbps</div>
                        <div style="margin-top: 10px;">Download</div>
                    </div>
                    <div class="speed-meter">
                        <svg width="150" height="150" viewBox="0 0 150 150">
                            <circle cx="75" cy="75" r="60" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="10"/>
                            <circle cx="75" cy="75" r="60" fill="none" stroke="var(--primary)" stroke-width="10" 
                                    stroke-dasharray="377" stroke-dashoffset="226" stroke-linecap="round"
                                    transform="rotate(-90 75 75)"/>
                        </svg>
                        <div class="speed-value">150 Mbps</div>
                        <div style="margin-top: 10px;">Upload</div>
                    </div>
                    <div class="speed-meter">
                        <svg width="150" height="150" viewBox="0 0 150 150">
                            <circle cx="75" cy="75" r="60" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="10"/>
                            <circle cx="75" cy="75" r="60" fill="none" stroke="#ff9800" stroke-width="10" 
                                    stroke-dasharray="377" stroke-dashoffset="30" stroke-linecap="round"
                                    transform="rotate(-90 75 75)"/>
                        </svg>
                        <div class="speed-value">12 ms</div>
                        <div style="margin-top: 10px;">Ping</div>
                    </div>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <span>Quick Actions</span>
                </div>
                <div style="display: flex; gap: 1rem;">
                    <button class="btn btn-3d">Restart Router</button>
                    <button class="btn btn-3d">Run Speed Test</button>
                    <button class="btn btn-3d">Block Device</button>
                    <button class="btn btn-3d">Guest Network</button>
                </div>
            </div>
        </div>
    </div>
    
    <script>
        // Simple animation for device nodes
        document.querySelectorAll('.device-node').forEach((node, index) => {
            if(index > 0) {
                const delay = index * 0.2;
                node.style.animationDelay = `${delay}s`;
                
                // Create connection lines (would be better with canvas/SVG)
                const router = document.querySelector('.device-node:first-child');
                const line = document.createElement('div');
                line.style.position = 'absolute';
                line.style.backgroundColor = 'rgba(3, 218, 198, 0.3)';
                line.style.height = '2px';
                line.style.transformOrigin = '0 0';
                line.style.zIndex = '-1';
                
                const routerRect = router.getBoundingClientRect();
                const nodeRect = node.getBoundingClientRect();
                const networkViz = document.querySelector('.network-visualization');
                const vizRect = networkViz.getBoundingClientRect();
                
                const routerX = routerRect.left + routerRect.width/2 - vizRect.left;
                const routerY = routerRect.top + routerRect.height/2 - vizRect.top;
                const nodeX = nodeRect.left + nodeRect.width/2 - vizRect.left;
                const nodeY = nodeRect.top + nodeRect.height/2 - vizRect.top;
                
                const length = Math.sqrt(Math.pow(nodeX - routerX, 2) + Math.pow(nodeY - routerY, 2));
                const angle = Math.atan2(nodeY - routerY, nodeX - routerX) * 180 / Math.PI;
                
                line.style.width = `${length}px`;
                line.style.left = `${routerX}px`;
                line.style.top = `${routerY}px`;
                line.style.transform = `rotate(${angle}deg)`;
                
                networkViz.appendChild(line);
            }
        });
    </script>
</body>
</html>
