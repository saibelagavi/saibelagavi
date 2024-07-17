<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sainath M. Belagavi - Holographic Profile</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        body, html {
            margin: 0;
            padding: 0;
            height: 100%;
            font-family: 'Arial', sans-serif;
            background: #000;
            color: #fff;
            overflow: hidden;
        }
        #canvas-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
        .content {
            position: relative;
            z-index: 1;
            padding: 20px;
            max-width: 800px;
            margin: 0 auto;
            backdrop-filter: blur(5px);
            background: rgba(0, 0, 0, 0.5);
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.5);
        }
        h1, h2 {
            color: #0ff;
            text-shadow: 0 0 10px #0ff;
        }
        .skill-orb {
            display: inline-block;
            padding: 10px 20px;
            margin: 5px;
            background: linear-gradient(45deg, #00f, #f0f);
            border-radius: 50px;
            box-shadow: 0 0 15px #f0f;
            transition: all 0.3s ease;
        }
        .skill-orb:hover {
            transform: scale(1.1);
            box-shadow: 0 0 25px #f0f;
        }
        .project-cube {
            width: 150px;
            height: 150px;
            margin: 20px;
            display: inline-block;
            perspective: 600px;
        }
        .cube-face {
            width: 100%;
            height: 100%;
            position: absolute;
            background: rgba(0, 255, 255, 0.1);
            border: 2px solid #0ff;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            backface-visibility: hidden;
            transition: transform 0.5s;
        }
    </style>
</head>
<body>
    <div id="canvas-container"></div>
    <div class="content">
        <h1>Sainath M. Belagavi</h1>
        <p>Quantum Innovator | Neural Architect | Holographic Engineer</p>
        
        <h2>Skill Nexus</h2>
        <div class="skill-orb">QuantumAI</div>
        <div class="skill-orb">NeuralWeb</div>
        <div class="skill-orb">BioSynth</div>
        <div class="skill-orb">HoloDesign</div>
        
        <h2>Project Cubes</h2>
        <div class="project-cube" id="cube1">
            <div class="cube-face">NeuroDrive</div>
        </div>
        <div class="project-cube" id="cube2">
            <div class="cube-face">TimeWarp</div>
        </div>
        <div class="project-cube" id="cube3">
            <div class="cube-face">NeuroRehab</div>
        </div>
    </div>

    <script>
        // Three.js background
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.getElementById('canvas-container').appendChild(renderer.domElement);

        const geometry = new THREE.TorusKnotGeometry(10, 3, 100, 16);
        const material = new THREE.MeshBasicMaterial({ color: 0x00ffff, wireframe: true });
        const torusKnot = new THREE.Mesh(geometry, material);
        scene.add(torusKnot);

        camera.position.z = 30;

        function animate() {
            requestAnimationFrame(animate);
            torusKnot.rotation.x += 0.01;
            torusKnot.rotation.y += 0.01;
            renderer.render(scene, camera);
        }
        animate();

        // Cube rotation
        const cubes = document.querySelectorAll('.project-cube');
        cubes.forEach(cube => {
            cube.addEventListener('mousemove', (e) => {
                const rect = cube.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                const rotateY = (x / rect.width - 0.5) * 90;
                const rotateX = (y / rect.height - 0.5) * 90;
                cube.style.transform = `rotateY(${rotateY}deg) rotateX(${rotateX}deg)`;
            });
            cube.addEventListener('mouseleave', () => {
                cube.style.transform = 'rotateY(0) rotateX(0)';
            });
        });
    </script>
</body>
</html>
