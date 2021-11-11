<script>
    import TextToSpeech from "./textToSpeech.svelte";
    import GetLanguages from "./GetLanguages.svelte";
</script>

<h1>Convert text to speech.</h1>

<div>
    <GetLanguages/>
    <TextToSpeech/>
</div>


<style>
    h1{
        text-align: center;
        font-size: 75px;
    }
    div{
        text-align: center;
    }
</style>
