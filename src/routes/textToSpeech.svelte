<script>
    import { storeLanguage } from './stores';

    let userText;
    let englishText;
    var speech;

    //This gets the translated text and the selected language and speaks it out.
    function textToSpeech(){
        speech = new SpeechSynthesisUtterance(userText);
        speech.lang = $storeLanguage;
        window.speechSynthesis.speak(speech);
    }
    //This connects to the free translator api.
    async function translateText(){
        if( $storeLanguage != ""){
            const res = await fetch("https://translate.argosopentech.com/translate", {
                        method: "POST",
                        body: JSON.stringify({
                            q: englishText,
                            source: "en",
                            target: $storeLanguage,
                        }),
                        headers: { "Content-Type": "application/json" }
                    }).catch(() => {
                        alert("There is a problem, please check your internet connection and try again.");
                    });
            var translation = await res.json(); 
            userText = translation.translatedText;
        }
        else{
           alert("Please Choose a Language")
        }

    }

    function ClearBoxes(){
        speech, userText = "";
        englishText = "";
    }
</script>

<label for="inputs">Enter your text below.</label>

<br>
<!-- svelte-ignore a11y-autofocus -->
<textarea bind:value= { englishText } id='inputs' rows="5" cols ="50" placeholder="Enter your text here." autofocus=true></textarea><br>
<button on:click={ translateText }>Translate</button><br>
<button on:click={ textToSpeech }>Play</button>
<button on:click= { ClearBoxes }>Clear</button><br>

<label for="inputs1">Translated text</label>
<br>
<textarea bind:value={ userText } id='inputs1' rows="5" cols="50" disabled placeholder="Translation will be here."></textarea>
<br>


<style>
    label{
        font-size:30px;
        font-weight: bold;
        color: darkred;
        padding-bottom: 100px;
    }
    textarea{
        background-color:rgb(207, 147, 124);
        color: black;
        font-size: large;
        font-weight: bolder;
        font-family: Arial, Helvetica, sans-serif;
        text-align: center;
        padding-top: 41px;
        border-radius: 25px;
        width: 75%;
        height: auto;
        
    }
    button{
        background-color:burlywood;
        border-radius: 25px;
        margin: 15px;
        width: 60%;
        height: 30px;
    }
</style>






