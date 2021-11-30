<script>
    import TextToSpeech from "./textToSpeech.svelte";
    import GetLanguages from "./GetLanguages.svelte";
    import Navbar from "./navbar.svelte";
</script>

<div id="nav">
    <Navbar/> 
    <GetLanguages/>
    <br>
    <br>
    <br>
    <br>
</div>

<div id="main">
    <TextToSpeech/>
</div>


<style>
    #nav{
        position: absolute;
        left: 50%;
        top: 10%;
        transform: translate(-50%, -50%);
        width: 100%;
    }
    #main{
        text-align: center;
        position: absolute;
        left: 50%;
        top: 55%;
        margin-top: 100px;
        transform: translate(-50%, -50%);
        background-color: white;
        width: 40%;
        height: 100vh;
    }
</style>
