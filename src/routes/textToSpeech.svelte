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
                    });
            var translation = await res.json(); 
            userText = translation.translatedText;
        }
        else{
           window.alert("Please Choose a Language")
        }

    }

    function ClearBoxes(){
        speech, userText = "";
        englishText = "";
    }
</script>

<label for="inputs">Enter your text below.</label>
<button on:click={translateText}>Click to translate</button>

<br>
<!-- svelte-ignore a11y-autofocus -->
<textarea bind:value= { englishText } id='inputs' rows="10" cols ="65" placeholder="Enter your text" autofocus=true></textarea><br>
<button on:click= { ClearBoxes }>Clear the text boxes</button><br>

<label for="inputs1">Translated text</label>
<br>
<textarea bind:value={ userText } id='inputs1' rows="10" cols="65" disabled placeholder="Translation will be here."></textarea>
<br>
<button on:click={textToSpeech}>Click to hear</button>

<style>
    label{
        font-size:30px;
        font-weight: bold;
        color: darkred;
        padding-bottom: 100px;
    }
    textarea{
        background-color:orangered;
        color: black;
        font-size: large;
        font-weight: bolder;
        font-family: Arial, Helvetica, sans-serif;
        text-align: center;
        padding-top: 41px;
        border-radius: 25px;
    }
    button{
        background-color: coral;
        border-radius: 25px;
        margin: 15px;
    }
</style>






