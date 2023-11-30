---
layout: default
---
<html>
    <head>
        <style>
            img {
                display: block;
                margin: 0;
                padding: 0;
                border: none;
            }

            table {
                width: 100%;
                padding: 10px;
                border: none;
            }

            td {
                padding: 10px;
                vertical-align: top;
                border: none;
            }

            #leftColumn {
                width: 25%;
                text-align: center;
            }

            #leftColumn button {
                display: block;
                margin-bottom: 10px;
                width: 100%;
                padding: 15px;
                border: none;
                border-radius: 10px;
                font-size: 16px;
                color: #fff;
                cursor: pointer;
                transition: background-color 0.3s ease-in-out;
            }

            #centerColumn {
                width: 25%;
            }

            #rightColumn {
                width: 100%;
                text-align: center;
            }

            .darken-hover:hover {
            filter: brightness(90%);
            }

            .cycle-hover {
                transition: background-color 0.5s ease-in-out;
            }
        </style>
    </head>
<body>
    <table>
        <tr>
            <td id="leftColumn">
                <button onclick="show(0)" style="background-color: #A0CBE8;">Miscellaneous</button>
                <button onclick="show(1)" style="background-color: #FFBE7D;">Ice Field</button>
                <button onclick="show(2)" style="background-color: #59A14F;">Ice Cap</button>
                <button onclick="show(3)" style="background-color: #8CD17D;">Outlet Glacer</button>
                <button onclick="show(4)" style="background-color: #B6992D;">Valley Glacier</button>
                <button onclick="show(5)" style="background-color: #F1CE63;">Mountain Glacier</button>
                <button onclick="show(6)" style="background-color: #499894;">Glacieret and Snowfield</button>
                <button onclick="show(7)" style="background-color: #86BCB6;">Ice Shelf</button>
                <button onclick="show(8)" style="background-color: #E15759;">Rock Glacier</button>
                <button onclick="show(9)" onmouseover="cycleHoverColor(this)" style="background-color: black;">All</button>
            </td>
            <td id="centerColumn">
                <div id="textDisplay"></div>
            </td>
            <td id="rightColumn">
                <img id="imageDisplay" src="assets/image/glacier.png" alt="Image">
            </td>
        </tr>
    </table>
    <img src="https://media.springernature.com/full/springer-static/image/prt%3A978-90-481-2642-2%2F17/MediaObjects/978-90-481-2642-2_17_Part_Fig5-453_HTML.gif">
</body>
<script>
    const glacierData = [
        {image: 'assets/image/0_miscellaneous.png',
            text: 'Any type of glacier not listed elsewhere.',
            color: '#A0CBE8'},
        {image: 'assets/image/2_ice_field.png',
            text: 'Ice masses of the sheet or blanket type with a thickness that is insufficient to obscure the subsurface topography.',
            color: '#FFBE7D'},
        {image: 'assets/image/3_ice_cap.png',
            text: 'Dome-shaped ice masses with radial flow.',
            color: '#59A14F'},
        {image: 'assets/image/4_outlet_glacier.png',
            text: 'Drains an ice sheet, ice field, or ice cap, usually of valley glacier form; the catchment area may not be easily defined.',
            color: '#8CD17D'},
        {image: 'assets/image/5_valley_glacier.png',
            text: 'Flows down a valley; the catchment area is well defined',
            color: '#B6992D'},
        {image: 'assets/image/6_mountain_glacier.png',
            text: 'Cirque, niche type, crater type, or hanging glacier; also includes ice aprons and groups of small units.',
            color: '#F1CE63'},
        {image: 'assets/image/7_glacieret_and_snowfield.png',
            text: 'Small ice masses of indefinite shape in hollows, river beds, or on protected slopes that have developed from snow drift, avalanches, and/or particularly heavy accumulation in certain years. Usually no marked flow pattern is visible; and it has been in existence for at least two consecutive years.',
            color: '#499894'},
        {image: 'assets/image/8_ice_shelf.png',
            text: 'Floating ice sheet of considerable thickness attached to a coast nourished by a glacier or glaciers; snow accumulation on its surface or bottom freezing.',
            color: '#86BCB6' },
        {image: 'assets/image/9_rock_glacier.png',
            text: 'Lava-stream-like debris mass containing ice in several possible forms and moving slowly downslope.',
            color: '#E15759'
        },
    ];

    function show(i) {
        const data = glacierData[i];
        document.getElementById('textDisplay').innerHTML = data.text;
        document.getElementById('imageDisplay').src = data.image;
    }

    document.addEventListener('DOMContentLoaded',
        function () {
            const buttons = document.querySelectorAll('button');
            buttons.forEach(function (button) {
                button.classList.add('darken-hover');
        });
    });

    function cycleHoverColor(button) {
        let i = 0;
        const intervalId = setInterval(updateColor, 1000);
        button.addEventListener('mouseleave', function () {
            clearInterval(intervalId);
            button.style.backgroundColor = 'black';
        });

        function updateColor() {
            i = (i + 1) % glacierData.length;
            button.style.backgroundColor = glacierData[i].color;
        }
    }
</script>
</html>
