# コードを編集する例

OpenAI の [edits](https://openai.com/blog/gpt-3-edit-insert/) エンドポイントは、コードの編集に特に役立ちます。

補完とは異なり、編集は編集するテキストと指示の 2 つの入力を受け取ります。

たとえば、Python 関数を編集する場合は、関数のテキストと「docstring を追加」などの指示を提供できます。

`code-davinci-edit-001` へのテキスト入力例:

```python
def tribonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    elif n == 2:
        return 1
    elif n == 3:
        return 2
    else:
        return tribonacci(n-1) + tribonacci(n-2) + tribonacci(n-3)
```

命令入力の例:

```テキスト
ドキュメントストリングを追加してください
```

```テキスト
Python 3.9の規約を利用した型付けを追加をしてください
```

```テキスト
実行時間を改善してください
```

```テキスト
テストを追加してください
```

```テキスト
JavaScript (または Rust、Lisp、または任意の言語) に翻訳てください
```

実行時間を改善して JavaScript に変換した出力例:

```JavaScript
function tribonacci(n) {
  let a = 0;
  let b = 1;
  let c = 1;
  for (let i = 0; i < n; i++) {
    [a, b, c] = [b, c, a + b + c];
  }
  return a;
}
```

ご覧のとおり `code-davinci-edit-001` は、関数の実行時間を指数関数から線形に短縮し、Python から JavaScript に変換することに成功しました。

[OpenAI Playground](https://beta.openai.com/playground?mode=edit&model=code-davinci-edit-001) で `code-davinci-edit-001` を使用してコード編集を試してください。

<!--
# Code editing example

OpenAI's [edits](https://openai.com/blog/gpt-3-edit-insert/) endpoint is particularly useful for editing code.

Unlike completions, edits takes two inputs: the text to edit and an instruction.

For example, if you wanted to edit a Python function, you could supply the text of the function and an instruction like "add a docstring".

Example text input to `code-davinci-edit-001`:

```python
def tribonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    elif n == 2:
        return 1
    elif n == 3:
        return 2
    else:
        return tribonacci(n-1) + tribonacci(n-2) + tribonacci(n-3)
```

Example instruction inputs:

```text
add a docstring
```

```text
Add typing, using Python 3.9 conventions
```

```text
improved the runtime
```

```text
Add a test.
```

```text
Translate to JavaScript (or Rust or Lisp or any language you like)
```

Example output after improving the runtime and translating to JavaScript:

```JavaScript
function tribonacci(n) {
  let a = 0;
  let b = 1;
  let c = 1;
  for (let i = 0; i < n; i++) {
    [a, b, c] = [b, c, a + b + c];
  }
  return a;
}
```

As you can see, `code-davinci-edit-001` was able to successfully reduce the function's runtime from exponential down to linear, as well as convert from Python to JavaScript.

Experiment with code editing using `code-davinci-edit-001` in the [OpenAI Playground](https://beta.openai.com/playground?mode=edit&model=code-davinci-edit-001).
-->
