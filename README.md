# Qwiet AI

```
 ██████╗ ██╗    ██╗██╗███████╗████████╗ █████╗ ██╗
██╔═══██╗██║    ██║██║██╔════╝╚══██╔══╝██╔══██╗██║
██║   ██║██║ █╗ ██║██║█████╗     ██║   ███████║██║
██║▄▄ ██║██║███╗██║██║██╔══╝     ██║   ██╔══██║██║
╚██████╔╝╚███╔███╔╝██║███████╗   ██║██╗██║  ██║██║
 ╚══▀▀═╝  ╚══╝╚══╝ ╚═╝╚══════╝   ╚═╝╚═╝╚═╝  ╚═╝╚═╝
```

Integrate [Qwiet.AI](https://docs.shiftleft.io/home) in your GitHub workflow.

## Usage

Autodetect languages storing CPGs in a directory called `cpg_out`

```
- uses: QwietAI/qwiet-action@main
  with:
    out_dir: "/github/workspace/cpg_out"
```

Use `lang` argument to force the language type. Comma separated values are accepted.

```
- uses: QwietAI/qwiet-action@main
  with:
    out_dir: "/github/workspace/cpg_out"
    lang: java
```

To export the generated CPGs to `dot` format, set the environment variable `CPG_EXPORT`.

```
- uses: QwietAI/qwiet-action@main
  with:
    out_dir: "/github/workspace/cpg_out"
    lang: java
  env:
    CPG_EXPORT: true
```

To customize the export representation and format use the environment variables `CPG_EXPORT_REPR` and `CPG_EXPORT_FORMAT`. Refer to the [source](https://github.com/AppThreat/cpggen/blob/main/cpggen/cli.py#L133) for all supported values.

Optionally, the upload the generated CPGs as build artifacts use the below step.

```
- name: Upload cpg
  uses: actions/upload-artifact@v1.0.0
  with:
    name: cpg
    path: cpg_out
```

## Languages supported

| Language    | Requires build |
| ----------- | -------------- |
| C           | No             |
| C++         | No             |
| Java        | No (\*)        |
| Scala       | Yes            |
| Jsp         | Yes            |
| Jar/War     | No             |
| JavaScript  | No             |
| TypeScript  | No             |
| Kotlin      | No (\*)        |
| Php         | No             |
| Python      | No             |
| C# / dotnet | Yes            |
| Go          | Yes            |

(\*) - Precision could be improved with dependencies

## Environment variables

| Name          | Purpose                              |
| ------------- | ------------------------------------ |
| AT_DEBUG_MODE | Set to debug to enable debug logging |

## License

Apache-2.0
