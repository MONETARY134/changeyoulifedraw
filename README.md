# changeyoulifedraw
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Shapes and Colors</title>
    <style>
        .shape {
            display: inline-block;
            width: 50px;
            height: 50px;
            margin: 10px;
        }

        .triangle {
            width: 0;
            height: 0;
            border-left: 25px solid transparent;
            border-right: 25px solid transparent;
            border-bottom: 50px solid;
        }

        .square {
            background-color: currentColor;
        }

        .circle {
            border-radius: 50%;
            background-color: currentColor;
        }

        .star {
            clip-path: polygon(
                50% 0%, 
                61% 35%, 
                98% 35%, 
                68% 57%, 
                79% 91%, 
                50% 70%, 
                21% 91%, 
                32% 57%, 
                2% 35%, 
                39% 35%
            );
            background-color: currentColor;
        }

        .heart {
            position: relative;
            width: 50px;
            height: 50px;
            background-color: currentColor;
            transform: rotate(-45deg);
        }

        .heart:before,
        .heart:after {
            content: "";
            position: absolute;
            width: 50px;
            height: 50px;
            background-color: inherit;
            border-radius: 50%;
            top: 0;
        }

        .heart:before {
            left: 25px;
        }

        .heart:after {
            top: -25px;
        }

        #generate-btn {
            margin: 20px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }

        #container {
            display: flex;
            flex-wrap: wrap;
        }
    </style>
</head>
<body>
    <button id="generate-btn">Generate Random Shape</button>
    <div id="container"></div>

    <script>
        const numbers = [0, 1, 9, 99, 100];
        const shapes = ['triangle', 'square', 'circle', 'star', 'heart'];
        const colors = ['black', 'green', 'yellow', 'blue', 'red'];

        const container = document.getElementById('container');
        const button = document.getElementById('generate-btn');

        function getRandomElement(array) {
            return array[Math.floor(Math.random() * array.length)];
        }

        function generateRandomShape() {
            const number = getRandomElement(numbers);
            const shape = getRandomElement(shapes);
            const color = getRandomElement(colors);

            const shapeElement = document.createElement('div');
            shapeElement.classList.add('shape', shape);
            shapeElement.style.color = color;

            const label = document.createElement('p');
            label.textContent = number;
            label.style.textAlign = 'center';

            const wrapper = document.createElement('div');
            wrapper.appendChild(shapeElement);
            wrapper.appendChild(label);
            container.appendChild(wrapper);
        }

        button.addEventListener('click', generateRandomShape);
    </script>
</body>
</html>
