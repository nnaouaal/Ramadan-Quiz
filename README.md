<!DOCTYPE html>
<html>
<head>
    <style>
        .section {
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        #section1 {
            background-color: green;
        }
        #section2 {
            display: none;
        }
    </style>
</head>
<body>
    <div id="section1" class="section">
        <button onclick="toggleSections()">Ir a la sección 2</button>
    </div>
    <div id="section2" class="section">
        <button onclick="toggleSections()">Volver a la sección 1</button>
    </div>

    <script>
        function toggleSections() {
            var section1 = document.getElementById('section1');
            var section2 = document.getElementById('section2');
            if (section1.style.display === 'none') {
                section1.style.display = 'flex';
                section2.style.display = 'none';
            } else {
                section1.style.display = 'none';
                section2.style.display = 'flex';
            }
        }
    </script>
</body>
</html>

