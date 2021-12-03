<script>
    import { storeLanguage } from './stores';

    let selectedLang;
    
    // This just sets the language in the svelte store 
    function LanguageSelection(){
        storeLanguage.set(selectedLang);
    }

</script>

<!--Below is the list of languages available through the free api at LibreTranslate-->
<select name = "language" id="languageSelect" bind:value={ selectedLang }  on:change= { LanguageSelection } >
    <option selected disabled>Choose a language</option>
    <option value="en">English</option>
    <option value="fr">French</option>
    <option value="es">Spanish</option>
    <option value="zh">Chinese</option>
    <option value="de">German</option>
    <option value="hi">Hindi</option>
    <option value="id">Indonesian</option>
    <option value="ga">Irish</option>
    <option value="it">Italian</option>
    <option value="ja">Japanese</option>
    <option value="ko">Korean</option>
    <option value="pl">Polish</option>
    <option value="pt">Portuguese</option>
    <option value="ru">Russian</option>
    <option value="tr">Turkish</option>
    <option value="vi">Vietnamese</option>
</select>

<style>
    select{
        background-color:burlywood;
        border-radius: 25px;
        position: absolute;
        left: 50%;
        transform: translate(-50%);
        width: 15%;
        height: 10%;
    }
</style>