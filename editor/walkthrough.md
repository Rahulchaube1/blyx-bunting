## Count requests by waiting time

Supply finite strictly increasing boundaries. A value exactly on a boundary belongs to the bucket above it. Bucket −1 counts missing or non-finite values. An empty boundary vector represents all finite values. The table generator validates boundaries before writing any markup. The caller supplies the HTML document around the table.

1. Open an empty file named `bunting-demo.blyx`.
2. Type `blyx-bunting-demo` and select **Bunting — runnable example**. You can also use **Snippets: Fill File with Snippet**.
3. Choose **Blyx: Run File** from the command palette. Change an argument near the end of `fn main()` to try another input.

Expected output

```text
2
2
2
```

[Work through the example in the browser](https://www.blyx-lang.space/play?example=package-bunting)
