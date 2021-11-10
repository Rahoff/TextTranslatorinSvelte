<script>
    import { storeLanguage } from './stores';
    let userText;
    let englishText;

    function textToSpeech(){
        const speech = new SpeechSynthesisUtterance(userText);
        speech.lang = $storeLanguage;
        window.speechSynthesis.speak(speech);
    }
    async function translateText(){
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
</script>

<label for="inputs">Enter text below:</label>
<button on:click={translateText}>Click to translate</button>
<button onclick="document.getElementById('inputs').value = ''">Clear User Input</button>
<br>
<textarea bind:value= { englishText } id='inputs' rows="15" cols ="65" placeholder="Enter your text"></textarea><br>


<label for="inputs1">Translated text:</label>
<!-- <button onclick="document.getElementById('inputs1').value = ''">Clear Translation</button> -->
<br>
<textarea bind:value={ userText } id='inputs1' rows="15" cols="65" disabled placeholder="Translation will be here."></textarea>
<br><br>
<button on:click={textToSpeech}>Click to hear</button>








