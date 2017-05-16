### `.value` 

`Value` returns the value of an option for example a radio, checkbox, text area or **input form**. `Value` is a property that belongs to the `html element object` as shown in the image below.

![value-example](http://i.imgur.com/EZtgsXz.png)

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

### Notice `.value` only works with certain HTML element objects

**`.value`** only works again with **`text area`**, **`options`** for **`check boxes`**, **`radios`** or **`input forms`**. It also works for the **`progress`** and **`meter`** elements for graphs or loading animations. Check out the example below where I try to access `.value` on a `p` tag. It does not work, if we perform `console.dir()` on the `p` element we notice `.value` is not listed in the properties

![value-lacking](http://i.imgur.com/pkB8TKr.png)
