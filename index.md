---
layout: default
---
<html lang="en">
<head>
    <style>
          img {
    display: block;
    margin: 0;
    padding: 0;
    border: none;
  }

        table {
            padding: 10px;
            border: none;
        }

        td {
            padding: 10px;
            vertical-align: top;
            border: none;
        }

        #leftColumn {
            width: 15%;
            text-align: center;
        }
        #centerColumn {
            width: 15%;
        }
       #rightColumn {
            width: 70%;
            text-align: center;
        }

        /* Updated styles for buttons */
        #leftColumn button {
            display: block;
            margin-bottom: 10px; /* Increased margin for spacing */
            width: 100%; /* Make buttons fill the width of the column */
            padding: 15px;
            border: none;
            border-radius: 10px; /* Increased border-radius for rounded edges */
            font-size: 16px; /* Increased font size */
            color: #fff;
            cursor: pointer;
            transition: background-color 0.3s; /* Smooth hover effect */
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
            <button onclick="showGlacier(0)" style="background-color: #A0CBE8;">Miscellaneous</button>
            <button onclick="showGlacier(1)" style="background-color: #FFBE7D;">Ice Field</button>
            <button onclick="showGlacier(2)" style="background-color: #59A14F;">Ice Cap</button>
            <button onclick="showGlacier(3)" style="background-color: #8CD17D;">Outlet Glacer</button>
            <button onclick="showGlacier(4)" style="background-color: #B6992D;">Valley Glacier</button>
            <button onclick="showGlacier(5)" style="background-color: #F1CE63;">Mountain Glacier</button>
            <button onclick="showGlacier(6)" style="background-color: #499894;">Glacieret and Snowfield</button>
            <button onclick="showGlacier(7)" style="background-color: #86BCB6;">Ice Shelf</button>
            <button onclick="showGlacier(8)" style="background-color: #E15759;">Rock Glacier</button>
            <button onclick="showGlacier(9, 'assets/image/glacier.png', 'Description for All Glaciers.')" onmouseover="cycleHoverColor(this)" style="background-color: black;">All</button>
        </td>
        <td id="centerColumn">
            <div id="textDisplay"></div>
        </td>
        <td id="rightColumn">
            <img id="imageDisplay" src="assets/image/glacier.png" alt="Image">
        </td>
    </tr>
</table>

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

function showGlacier(index, customImage, customText) {
    const imageDisplay = document.getElementById('imageDisplay');
    const textDisplay = document.getElementById('textDisplay');
    const buttons = document.getElementById('leftColumn').getElementsByTagName('button');

    if (typeof index === 'number' && index >= 0 && index < glacierData.length) {
        const data = glacierData[index];
        imageDisplay.src = data.image;
        textDisplay.innerHTML = data.text;
    }
}



    function show(imageName, text) {
        const image = document.getElementById('imageDisplay');
        image.src = imageName;

        const textDisplay = document.getElementById('textDisplay');
        textDisplay.innerHTML = text;
    }

  // Apply darken-hover class and hover effect to all buttons
  document.addEventListener('DOMContentLoaded', function () {
    const buttons = document.querySelectorAll('button');
    buttons.forEach(function (button) {
      button.classList.add('darken-hover');
      const originalColor = button.style.backgroundColor;
    });
  });
  function cycleHoverColor(button) {
    let index = 0;

    // Function to update color on hover
    function updateColor() {
        index = (index + 1) % glacierData.length;
        button.style.backgroundColor = glacierData[index].color;
    }

    // Set interval to update color every 1000ms (1 second)
    const intervalId = setInterval(updateColor, 1000);

    // Clear interval on mouseleave
    button.addEventListener('mouseleave', function () {
        clearInterval(intervalId);
        button.style.backgroundColor = 'black';
    });
}
</script>

</body>
</html>
