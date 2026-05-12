<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Kabaddi Scoreboard</title>
<link rel="stylesheet" href="style.css">
</head>

<body>

<div class="scoreboard">

<div class="team left">

<input type="text" id="team1Name" value="TEAM A">

<div class="score" id="score1">00</div>

<div class="buttons">
<button onclick="updateScore(1,1)">+</button>
<button onclick="updateScore(1,-1)">-</button>
</div>

</div>

<div class="center">

<div class="timer" id="timer">20:00</div>

<input type="text" id="half" value="1ST HALF">

<div class="timerButtons">
<button onclick="startTimer()">START</button>
<button onclick="stopTimer()">STOP</button>
<button onclick="resetTimer()">RESET</button>
</div>

</div>

<div class="team right">

<input type="text" id="team2Name" value="TEAM B">

<div class="score" id="score2">00</div>

<div class="buttons">
<button onclick="updateScore(2,1)">+</button>
<button onclick="updateScore(2,-1)">-</button>
</div>

</div>

</div>

<script src="script.js"></script>

</body>
</html>body{
margin:0;
overflow:hidden;
background:transparent;
font-family:Arial;
}

.scoreboard{
position:absolute;
bottom:20px;
left:50%;
transform:translateX(-50%);
width:1400px;
display:flex;
justify-content:space-between;
align-items:center;
}

.team{
width:420px;
height:180px;
border-radius:25px;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
color:white;
}

.left{
background:linear-gradient(135deg,#ff4d00,#ff9900);
}

.right{
background:linear-gradient(135deg,#0066ff,#00ccff);
}

.team input{
width:80%;
text-align:center;
font-size:30px;
font-weight:bold;
border:none;
border-radius:10px;
padding:8px;
}

.score{
font-size:70px;
font-weight:bold;
margin-top:10px;
}

.buttons{
margin-top:10px;
}

.buttons button{
width:60px;
height:50px;
margin:5px;
font-size:30px;
border:none;
border-radius:10px;
}

.center{
width:380px;
height:220px;
background:linear-gradient(135deg,#2d0036,#65007a);
border-radius:30px;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
color:white;
}

.timer{
font-size:60px;
font-weight:bold;
}

#half{
margin-top:10px;
font-size:22px;
text-align:center;
border:none;
border-radius:10px;
padding:6px;
}

.timerButtons{
margin-top:15px;
}

.timerButtons button{
padding:10px 15px;
margin:5px;
border:none;
border-radius:10px;
font-weight:bold;
}let score1 = 0;
let score2 = 0;

function updateScore(team,val){

if(team===1){

score1 += val;

if(score1<0){
score1=0;
}

document.getElementById("score1").innerText =
String(score1).padStart(2,'0');

}

else{

score2 += val;

if(score2<0){
score2=0;
}

document.getElementById("score2").innerText =
String(score2).padStart(2,'0');

}

}

let min = 20;
let sec = 0;

let timer;

function updateTimer(){

document.getElementById("timer").innerText =
String(min).padStart(2,'0')
+ ":" +
String(sec).padStart(2,'0');

}

function startTimer(){

clearInterval(timer);

timer = setInterval(()=>{

if(sec===0){

if(min===0){

clearInterval(timer);
return;

}

min--;
sec=59;

}

else{
sec--;
}

updateTimer();

},1000);

}

function stopTimer(){
clearInterval(timer);
}

function resetTimer(){

clearInterval(timer);

min=20;
sec=0;

updateTimer();

}

updateTimer();
