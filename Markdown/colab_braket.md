# Google Colaboratory で braket を使う

Colab でも `\braket{}` で $\braket{}$ を使いたい人向け

VSCode の Markdown 数式プレビューには [KaTeX](https://katex.org/docs/supported.html) が使用されていますが，Colab では [MathJax](https://docs.mathjax.org/en/latest/input/tex/macros/index.html) が使用されているらしいです．~~つまりこの記事の情報は「MathJax braket」でググればでてきます．~~

## 最初のセル

```latex
$$
\newcommand{\bra}[1]{⟨ #1 |}
\newcommand{\ket}[1]{| #1 ⟩}
\newcommand{\braket}[1]{\langle #1 \rangle}
$$
```

## 他のセル

```latex
$$
\braket{f|\hat{H}|i}
$$
```

$$
\braket{f|\hat{H}|i}
$$
