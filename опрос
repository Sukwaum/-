<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>Экологический опросник</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-firestore-compat.js"></script>

<style>

body{
font-family: Arial;
background:#f5f5f5;
margin:40px;
text-align:center;
}

.container{
max-width:700px;
margin:auto;
background:white;
padding:30px;
border-radius:10px;
box-shadow:0 0 10px rgba(0,0,0,0.1);
}

.question{
text-align:left;
margin-bottom:15px;
}

button{
padding:12px 25px;
background:#2e7d32;
color:white;
border:none;
border-radius:5px;
cursor:pointer;
}

canvas{
margin-top:40px;
}

</style>
</head>

<body>

<div class="container">

<h1>Экологический опросник</h1>

<form id="poll"></form>

<button onclick="sendVote()">Отправить</button>

<canvas id="chart"></canvas>

</div>

<script>

// вопросы

const questions = [

"Устраивает ли Вас уровень шума?",
"Устраивает ли Вас качество питьевой воды?",
"Устраивает ли Вас качество речных вод?",
"Устраивает ли Вас чистота улиц?",
"Достаточно ли зелёных насаждений?",
"Знаете ли Вы экологические программы?",
"Получаете ли достоверную информацию из СМИ?",
"Знаете ли Вы экологические проблемы?",
"Считаете ли охрану природы общим делом?",
"Приходилось ли бросать мусор?",
"Готовы участвовать в экологических акциях?",
"Готовы пересесть на велосипед?",
"Готовы участвовать в озеленении?",
"Готовы сортировать мусор?",
"Подкармливаете ли птиц зимой?"

]

// создание формы

const form=document.getElementById("poll")

questions.forEach((q,i)=>{

form.innerHTML+=
<div class="question">
${i+1}. ${q}<br>
<label><input type="radio" name="q${i}" value="yes"> Да</label>
<label><input type="radio" name="q${i}" value="no"> Нет</label>
</div>


})

// FIREBASE (нужно вставить свои данные)

const firebaseConfig = {

apiKey: "YOUR_KEY",
authDomain: "YOUR_DOMAIN",
projectId: "YOUR_PROJECT"

}

firebase.initializeApp(firebaseConfig)

const db = firebase.firestore()

function sendVote(){

let yes=0
let no=0

for(let i=0;i<questions.length;i++){

let options=document.getElementsByName("q"+i)

options.forEach(o=>{
if(o.checked){
if(o.value=="yes") yes++
else no++
}
})

}

db.collection("votes").add({
yes:yes,
no:no
})

drawChart(yes,no)

}

function drawChart(yes,no){

new Chart(document.getElementById("chart"),{

type:"pie",

data:{
labels:["Да","Нет"],
datasets:[{
data:[yes,no]
}]
}

})

}

</script>

</body>
</html>
