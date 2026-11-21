<img src="assets/logo.png" width="112" height="112" alt="Bunting bird logo">

# Blyx Bunting

Publish a distribution as a standalone HTML table with interval labels, counts and meters. Reuse the same bin definitions in reports and tests.

A colored chart alone can hide values from people navigating with assistive technology. W3C’s table guidance pairs data cells with headers. Bunting emits row and column headers and prints the count alongside every meter. [W3C WAI, Tables with One Header](https://www.w3.org/WAI/tutorials/tables/one-header/)

## Install and run

Install the Blyx 0.2.1 compiler and a Rust toolchain with a host linker. Clone the versioned release, then run its small example and regression suite.

```sh
cargo install --locked --version 0.2.1 blyxc
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-bunting.git
cd blyx-bunting
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

Expected output from the small example

```text
2
2
2
```

## Publish a support-queue report

Group eight first-reply waits at 5, 10 and 20 minutes. The resulting HTML page opens offline and exposes intervals, counts and shares as a table. Every observation contributes to one row.

```sh
blyxc native-run project.blyx
```

Write the report to disk with `blyxc native-run project.blyx > report.html`, then open report.html in a browser.

View the generated [report.html](https://www.blyx-lang.space/framework-examples/report.html).

[Run the portable example in the browser](https://www.blyx-lang.space/play?example=package-bunting) · [Follow the handbook exercise](https://doc.blyx-lang.space/guide/bunting) · [Download the release](https://github.com/Rahulchaube1/blyx-bunting/releases/tag/v0.1.0)

## Use the framework in your own project

From the folder containing your entry file, clone the release into `vendor/bunting`.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-bunting.git vendor/bunting
```

```blyx
use vendor::bunting::bunting;

fn main() {
    let waits = [0, 4, 5, 8, 10, 12];
    let edges = [5, 10];
    println!(bu_count(waits, edges, 0));
    println!(bu_count(waits, edges, 1));
    println!(bu_count(waits, edges, 2));
}
```

Run `blyxc native-run main.blyx`.

Supply finite strictly increasing boundaries. A value exactly on a boundary belongs to the bucket above it. Bucket −1 counts missing or non-finite values. An empty boundary vector represents all finite values. The table generator validates boundaries before writing any markup. The caller supplies the HTML document around the table.

| API | Behavior |
| --- | --- |
| `bu_valid(edges), bu_bucket(edges, value)` | Check boundaries and locate the value by binary search. |
| `bu_count(data, edges, bucket)` | Count observations in one bucket. An invalid request returns −1. |
| `bu_table(data, edges)` | Write a captioned HTML table with explicit counts and meter values. Returns false for invalid boundaries. |

## Contribute

When opening an issue, include the smallest reproducing Blyx input, the compiler version and the output you expected. [Source and issues](https://github.com/Rahulchaube1/blyx-bunting/issues) · [Blyx community](https://www.blyx-lang.space/community)

Dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
