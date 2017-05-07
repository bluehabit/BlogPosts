### .value 

`Value` returns the value of an option for example a radio, checkbox, text area or **input form**. 

```
<input type='radio' name='animal' value='giraffe'>
<label for ='giraffe'>giraffe</label>

<input type='radio' name='animal' value='walrus'>
<label for ='walrus'>walrus</label>

<input type='radio' name='animal' value='parakeet'>
<label for ='parakeet'>parakeet</label>

<textarea id='myText'>Some stuff in here</textarea>

<script>
var radio = document.querySelectorAll("input[name='animal'");
//radio[0].value -> giraffe
//radio[1].value -> walrus
//radio[2].value -> parakeet

var textArea = document.getElementById('myText');
//textArea.value 
//-> some stuff in here
</script>
```
