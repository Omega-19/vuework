<template>
    <header>
        <h1>{{message}}</h1>
    </header>
    <main>

        <article>
            <h2>First step</h2>
            <p>Ce site sera en quelque sorte un résumé de tout ce que j'ai vu dernièrement.</p>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Unde exercitationem totam optio rerum adipisci temporibus sequi quos qui expedita molestias.</p>
            <p>It is time to work. Lorem ipsum dolor, sit amet consectetur adipisicing elit. Harum dolore ipsa non debitis magnam. Velit!</p>

        </article>
        <article>
            <h2>Mon formulaire</h2>
        <form action="#" method="post">
            <fieldset>
                <legend>My description</legend>
                <label for="fname">firstName</label>
                <input type="text" id="fname" placeholder="Your firstName here" v-model="fname"><br>
                <!-- <p>Your message is: {{fname}}</p> -->
                
                <label for="lname">lastName</label>
                <input type="text" id="lname" placeholder="Your lastName here"><br>

                <label for="password">Password</label>
                <input type="password"  id="password" placeholder="Your password here">
            </fieldset>
        </form>
        </article>
        <article>
            <h2>Mon chronomètre</h2>
            <div id="chrono">
                <h3>Mon chronomètre en seconde</h3>
                <p>00:00:00</p>
                <button id="startbtn">Start</button>
                <button id="stopbtn">Stop</button>
                <button id="reset-btn">Reset</button>
            </div>
        </article>
    </main>

</template>

<style>
#startbtn{
background-color: green;
color: #fff;
}
#stopbtn{
    background-color: orangered;
    color: black;
    font-weight: 600;
}
#reset-btn{
    background-color: red;
    color: #fff;
}
h1{
    text-transform: uppercase;
    font-size: 2.5rem;
}
p{
    color: black;
    font-family: Arial, Helvetica, sans-serif;
    font-size: 1.5rem;
}
label{
    font-weight: 750;
    margin-right: 3rem;
}
input{
    border-radius: 2rem;
    padding: 0.5rem;
}
form{
line-height: 2.5rem;
}
</style>

<script>
let chronoDom;
// La tierce..
let chrono = {
    tierce: 0,
    seconde: 0,
    minute: 0,
}
let updateSpeed = 1000 / 60;
document.addEventListener("DOMContentLoaded", function(){
    let timerId;
chronoDom = document.querySelector("#chrono");
let domStartButton = document.querySelector("#startbtn");
let endtButton = document.querySelector("#stopbtn");
let resetButton = document.querySelector("#reset-btn");

    resetButton.addEventListener("click", function () {
        clearTimeout(timerId);
        chronoDom.innerText = "00 : 00 : 00";
        chrono.minute = 0;
        chrono.seconde = 0;
        chrono.tierce = 0;
    });
    domStartButton.addEventListener("click", function () {
        updateChrono();
    });

endtButton.addEventListener("click", function () {
        clearTimeout(timerId);
    });
    function updateChrono() {
    // incrementation
    if (chrono.tierce < 59) {
        chrono.tierce++;
    } else if (chrono.seconde < 59) {
        chrono.tierce = 0;
        chrono.seconde++;
    } else {
        chrono.seconde = 0;
        chrono.minute++;
    }
    //    on relance la mise à jour
    updateDisplay();
    // répétition du comptage
    timerId = setTimeout(updateChrono, updateSpeed);
}

function updateDisplay() {
    chronoDom.innerText =
        `${formatNumber(chrono.minute)} : ${formatNumber(chrono.seconde)} : ${formatNumber(chrono.tierce)}`;
}
function formatNumber(num) {
    return num < 10 ? "0" + num : num;
}

})

</script>
