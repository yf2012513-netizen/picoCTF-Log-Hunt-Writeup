### picoCTF - Log Hunt (General Skills) Writeup

A writeup for the picoCTF "Log Hunt" challenge.  
picoCTFの「Log Hunt」チャレンジの解説（Writeup）です。

### Challenge Overview / 問題概要

*   **Category / カテゴリ**: General Skills
*   **Difficulty / 難易度**: Easy
*   **Points / 配点**: 50 pts
*   **Description / 説明**: Our server seems to be leaking pieces of a secret flag in its logs. The parts are scattered and sometimes repeated. Can you reconstruct the original flag?

* * *

### Solution / 解法

### 1\. Extracting the flag fragments / フラグ断片の抽出

The log file contains timestamps, which prevent a simple `sort -u` from removing duplicate flag parts. To extract only the flag fragments (the 5th column in the log format), execute the following command:

ログファイルにはタイムスタンプが含まれているため、単純に `sort -u` を実行しても重複が排除されません。フラグの断片（ログの5列目）だけを抽出して重複を消去するために、以下のコマンドを実行します。

bash

    grep "INFO FLAGPART" server.log | awk '{print $5}' | sort -u
    

コードは注意してご使用ください。

### 2\. Output / 実行結果

Running the command will produce the following unique fragments sorted alphabetically:

コマンドを実行すると、重複が排除され、アルファベット順に並び替えられた以下の断片が出力されます。

text

    cedfa5fb}
    picoCTF{us3_
    sk1lls_
    y0urlinux_
    

コードは注意してご使用ください。

### 3\. Reconstructing the Flag / フラグの再構築

Reassemble the pieces to form a valid flag format that starts with `picoCTF{` and ends with `}`:

`picoCTF{` で始まり `}` で終わる正しいフラグの構造に合わせて、断片を順番に繋ぎ合わせます。

1.  `picoCTF{us3_`
2.  `y0urlinux_`
3.  `sk1lls_`
4.  `cedfa5fb}`

* * *

### Flag / フラグ

text

    [picoCTF FLAG HIDDEN]
    

コードは注意してご使用ください。
