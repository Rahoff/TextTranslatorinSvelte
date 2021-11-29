<script>
    import TextToSpeech from "./textToSpeech.svelte";
    import GetLanguages from "./GetLanguages.svelte";
    import Navbar from "./navbar.svelte";
</script>

<div id="nav">
    <Navbar/>
    <br>
    <br>
    <br>
    <br>
</div>


<div id="main">
    <GetLanguages/>
    <TextToSpeech/>
</div>


<style>
    #nav{
        position: absolute;
        left: 50%;
        top: 10%;
        transform: translate(-50%, -50%);
        width: max-content;
    }
    #main{
        text-align: center;
        position: absolute;
        left: 50%;
        top: 55%;
        transform: translate(-50%, -50%);
        background-color: white;
        
    }
</style>
