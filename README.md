<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ASCII Animace</title>
    <style>
        body { background: black; color: lime; font-family: monospace; white-space: pre; text-align: center; }
        pre { font-size: 8px; line-height: 8px; }
    </style>
</head>
<body>
    <pre id="ascii"></pre>

    <script>
        async function loadAnimation() {
            const response = await fetch("ascii_animation_high_res.txt");
            const text = await response.text();
            const frames = text.split("\n\n"); // Rozdělení na jednotlivé snímky
            let index = 0;

            function playAnimation() {
                document.getElementById("ascii").textContent = frames[index];
                index = (index + 1) % frames.length;
                setTimeout(playAnimation, 100); // 10 FPS
            }

            playAnimation();
        }

        loadAnimation();
    </script>
</body>
</html>
