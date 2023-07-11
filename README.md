# benchmark

This a tool to benchmark JS. Currently it's used by me in the Stackoverflow snippets.
It's not open-source yet, since the development is experimental with no caring about meaninful commits.

So here's a small tutor how to benchmark JS code on the Stackoverflow.
How to create a benchmark:  

Create a snippet and paste into the HTML section the following:

```
<script benchmark data-count="1">
    // data-count - number of cycles
    // then the common code for all solution until the first // @benchmark

    const str = 'Hello world'.repeat(1000000);

    // @benchmark string concat
    // 'string concat' - name/title of the solution
    // here could be any code for this solution that won't by cycled

    // @run
    // after @run the code will be cycled data-count times. you don't need @run if there's nothing to execute before the cycled code
    let inverted = '';
    for (let i = str.length - 1; i >= 0; i--) {
        inverted += str[i];
    }
    inverted; // this will be returned by eval

    // @benchmark looping array
    {
        const arr = str.split('');

        for (let i = 0, j = arr.length - 1; i < j; i++, j--) {
            [arr[i], arr[j]] = [arr[j], arr[i]];
        }

        arr.join('');
    }

</script>
<script src="https://cdn.jsdelivr.net/gh/silentmantra/benchmark/loader.js"></script>
```

The roadmap

1. more detailed documentation
2. more precise benchmarks with allowing to open a separate page in the browser and benchmark every solution on a page reload
   (the current design is to execute in a separate `<script>`).
4. go open-source

Please subscribe to the repository to get futher updates...
