# Javascript Excercise: Piano Keys

Simple emulation of piano player on website.

## Javascript
```
// The keys and notes variables store the piano keys
const keys = ['c-key', 'd-key', 'e-key', 'f-key', 'g-key', 'a-key', 'b-key', 'high-c-key', 'c-sharp-key', 'd-sharp-key', 'f-sharp-key', 'g-sharp-key', 'a-sharp-key'];
const notes = [];
keys.forEach(function(key){
  notes.push(document.getElementById(key));
})

// Write named functions that change the color of the keys below
function keyPlay(event){
  event.target.style.backgroundColor='#6df0c2';
}

function keyReturn(event){
  event.target.style.backgroundColor='';
}
// Write a named function with event handler properties
function eventAssignment(note){
  note.onmousedown=function(){
    keyPlay(event);
  }
  note.onmouseup=function(){
    keyReturn(event);
  }
}
// Write a loop that runs the array elements through the function
notes.forEach(eventAssignment);

// These variables store the buttons that progress the user through the lyrics
let nextOne = document.getElementById('first-next-line');
let nextTwo = document.getElementById('second-next-line');
let nextThree = document.getElementById('third-next-line');
let startOver = document.getElementById('fourth-next-line');

// This variable stores the '-END' lyric element
let lastLyric = document.getElementById('column-optional');

// These statements are "hiding" all the progress buttons, but the first one
nextTwo.hidden = true;
nextThree.hidden = true;
startOver.hidden= true;

// Write anonymous event handler property and function for the first progress button
nextOne.onclick=function(){
  nextTwo.hidden=false;
  nextOne.hidden=true;
  document.getElementById('letter-note-five').innerHTML='D';
  document.getElementById('letter-note-six').innerHTML='C';
}

// Write anonymous event handler property and function for the second progress button
nextTwo.onclick=function(){
  nextThree.hidden=false;
  nextTwo.hidden=true;
  document.getElementById('word-five').innerHTML='DEAR';
  document.getElementById('word-six').innerHTML='FRI-';
  lastLyric.style.display='inline-block';
  document.getElementById('letter-note-three').innerHTML='G';
  document.getElementById('letter-note-four').innerHTML='E';
  document.getElementById('letter-note-five').innerHTML='C';
  document.getElementById('letter-note-six').innerHTML='B';
}

// Write anonymous event handler property and function for the third progress button
nextThree.onclick=function(){
  startOver.hidden=false;
  nextThree.hidden=true;
  document.getElementById('word-one').innerHTML='HAP-';
  document.getElementById('word-two').innerHTML='PY';
  document.getElementById('word-three').innerHTML='BIRTH';
  document.getElementById('word-four').innerHTML='DAY';
  document.getElementById('word-five').innerHTML='TO';
  document.getElementById('word-six').innerHTML='YOU';
  document.getElementById('letter-note-one').innerHTML='F';
  document.getElementById('letter-note-two').innerHTML='F';
  document.getElementById('letter-note-three').innerHTML='E';
  document.getElementById('letter-note-four').innerHTML='C';
  document.getElementById('letter-note-five').innerHTML='D';
  document.getElementById('letter-note-six').innerHTML='C';
  lastLyric.style.display='none';
}

// This is the event handler property and function for the startOver button
startOver.onclick = function() {
  nextOne.hidden = false;
  startOver.hidden = true;
   document.getElementById('word-one').innerHTML = 'HAP-';
  document.getElementById('letter-note-one').innerHTML = 'G';
  document.getElementById('word-two').innerHTML = 'PY';
  document.getElementById('letter-note-two').innerHTML = 'G';
  document.getElementById('word-three').innerHTML = 'BIRTH-';
  document.getElementById('letter-note-three').innerHTML = 'A';
  document.getElementById('word-four').innerHTML = 'DAY';
  document.getElementById('letter-note-four').innerHTML = 'G';
  document.getElementById('word-five').innerHTML = 'TO';
  document.getElementById('letter-note-five').innerHTML = 'C';
  document.getElementById('word-six').innerHTML = 'YOU!';
  document.getElementById('letter-note-six').innerHTML = 'B';
}
```

## HTML
```
<!DOCTYPE html>
<html lang="en" >

<head>
  <meta charset="UTF-8">
  <link rel="stylesheet" href="style.css">
</head>

<body>
  <p class='title'>Piano Player</p>
  <p id='demo'>Follow the song below to play  the piano.</p>
  <section class="piano">
    <section id='c-key' class="key">
      <section class='keynote'>C</section>
    </section>
    <section id='c-sharp-key' class="black-key">
      <section class='black-keynote'>C#</section>
    </section>
    <section id='d-key' class="key">
      <section class='keynote'>D</section>
    </section>
    <section id='d-sharp-key' class="black-key">
      <section class='black-keynote'>D#</section>
    </section>
    <section id='e-key' class="key">
      <section class='keynote'>E</section>
    </section>
    <section id='f-key' class="key">
      <section class='keynote'>F</section>
    </section>
    <section id='f-sharp-key' class="black-key">
      <section class='black-keynote'>F#</section>
    </section>
    <section id='g-key' class="key">
      <section class='keynote'>G</section>
    </section>
    <section id='g-sharp-key' class="black-key">
      <section class='black-keynote'>G#</section>
    </section>
    <section id='a-key' class="key">
      <section class='keynote'>A</section>
    </section>
    <section id='a-sharp-key' class="black-key">
      <section class='black-keynote'>A#</section>
    </section>
    <section id='b-key' class="key">
      <section class='keynote'>B</section>
    </section>
    <section id='high-c-key' class="key">
      <div class='keynote'>C</div>
    </section>
  </section>

  <section id='lyrics'>
    <section id='column-one'>
      <section id="word-one">HAP-</section>
      <section id="letter-note-one">G</section>
    </section>
    <section id='column-two'>
      <section id="word-two">PY</section>
      <section id="letter-note-two">G</section>
    </section>
    <section id='column-three'>
      <section id="word-three">BIRTH-</section>
      <section id="letter-note-three">A</section>
    </section>
    <section id='column-four'>
      <section id="word-four">DAY</section>
      <section id="letter-note-four">G</section>
    </section>
    <section id='column-five'>
      <section id="word-five">TO</section>
      <section id="letter-note-five">C</section>
    </section>
    <section id='column-six'>
      <section id="word-six">YOU</section>
      <section id="letter-note-six">B</section>
    </section>
    <section id='column-optional' class='column-optional'>
      <section id="word-optional">END</section>
      <section id="letter-note-optional">A</section>
    </section>

    <button id="first-next-line">Line 2</button>
    <button id="second-next-line">Line 3</button>
    <button id="third-next-line">Line 4</button>
    <button id="fourth-next-line">Reset</button>
  </section>

  <script  src="main.js"></script>

</body>
</html>
```

## CSS
```
body{
    margin: 0;
    padding: 0;
    font-family: sans-serif;
    background: #ffc63f;
  }
  .title{
    font-size: 36px;
    margin-top: 10px;
    margin-bottom: 0px;
    padding: 0;
    color: #141c3a;
    text-transform: uppercase;
    letter-spacing: 2px;
    text-align: center;
  }
  #demo{
    text-align: center;
    font-size: 18px;
    margin-top: 15px;
    color: #141c3a;
    letter-spacing: 1px;
    font-style: italic;
  }
  .piano{
    width: 305px;
    height: 210px;
    display: block;
    margin: 0 auto;
    background-color: #fd4d3f;
    margin-top: 30px;
  }
  .key{
    width: 30px;
    height: 200px;
    display: inline-block;
    border: solid #141c3a 2px;
    box-shadow: 2px 5px;
    background-color: white;
    color: #141c3a;
  }
  .black-key{
    width: 25px;
    height: 100px;
    display: inline-block;
    background-color: #141c3a;
    color: white;
    position: absolute;
    margin-left: -12px;
    padding: 0px;
  }
  .keynote{
    width: 20px;
    height: 20px;
    text-align: center;
    display: block;
    margin: 0 auto;
    margin-top: 175px;
    color: #141c3a;
  }
  .black-keynote{
    width: 20px;
    height: 20px;
    text-align: center;
    display: block;
    margin: 0 auto;
    margin-top: 75px;
  }
  #lyrics{
    width: 400px;
    height: 240px;
    display: block;
    margin: 0 auto;
    padding-left: 20px;
    margin-top: 50px;
    background-color: #fd4d3f;
  }
  #column-one, #column-two, #column-three, #column-four, #column-five, #column-six, #column-optional{
    width: 90px;
    display: inline-block;
    text-align: center;
    margin-top: 30px;
  }
  #column-optional{
    display: none;
  }
  #word-one, #word-two, #word-three, #word-four, #word-five, #word-six, #word-optional{
    background-color: white;
    width: 90px;
    height: 25px;
    padding-top: 10px;
    letter-spacing: 5px;
    color: #141c3a;
  }
  #letter-note-one, #letter-note-two, #letter-note-three, #letter-note-four, #letter-note-five, #letter-note-six, #letter-note-optional{
    color: white;
    width: 25px;
    height: 25px;
    margin-top: 15px;
    margin-left: 35px;
  }
  #first-next-line, #second-next-line, #third-next-line, #fourth-next-line{
    width: 80px;
    height: 40px;
    font-size: 16px;
    position: absolute;
    margin-top: 30px;
    margin-left: 10px;
    border: none;
    background-color: #ffc63f;
    color: #141c3a;
    letter-spacing: 1px;
    cursor: pointer;
  }
```
