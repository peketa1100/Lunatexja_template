markdown
# 📘 技術書向け LaTeX テンプレート  
*A5 判・見開き対応・章扉／セクションデザイン／コラム／コード環境付き*

このリポジトリは、A5 判の技術書を制作するための **高品質 LaTeX テンプレート**です。  
章扉、セクション見出し、コラム、コード、ページレイアウトなどを完全にカスタムし、  
市販技術書に近いレイアウトを実現しています。

---

## 📁 ディレクトリ構成
```
project/
├── main.tex
├── preamble/
│   ├── packages.tex
│   ├── fonts.tex
│   ├── colors.tex
│   ├── layout.tex
│   ├── layoutA4report.tex ← A4レポート形式用
│   ├── header-footer.tex
│   ├── chapter-style.tex
│   ├── section-style.tex
│   ├── column-style.tex
│   └── code-style.tex
└── Lunatexja_main.tex   ← テンプレート解説書（LaTeX 版）
```

## 📂 preamble フォルダの説明

テンプレートのプリアンブルは役割ごとに分割され、保守性と再利用性を高めています。

### **preamble/packages.tex**  
使用するパッケージをまとめて読み込みます。  
日本語処理、色、図表、コード、見出し、余白、ヘッダ・フッタなどの基盤設定。

### **preamble/fonts.tex**  
欧文・和文フォントの設定。  
Noto 系フォントを中心に、本文・見出し・コード用フォントを定義。

### **preamble/colors.tex**  
テンプレートで使用する色（セクション帯、章扉、コラム、コード枠線など）を定義。

### **preamble/layout.tex**  
A5 判のページレイアウト、余白、行間などを設定。  
見開き（twoside）に最適化。

### **preamble/header-footer.tex**  
fancyhdr によるヘッダ・フッタ（柱）の設定。  
左ページに章タイトル、右ページにセクションタイトルを表示。

### **preamble/chapter-style.tex**  
章扉のデザイン。  
背景帯、章番号、章タイトルのレイアウトを定義。

### **preamble/section-style.tex**  
セクション見出しのデザイン。  
青帯＋黒文字＋ゴシック太字のスタイル。  
番号なしセクション用の `\plainsection` もここに含まれる。

### **preamble/column-style.tex**  
コラム（囲み記事）のデザイン。  
tcolorbox による枠線・背景色・アイコンなどを設定。

### **preamble/code-style.tex**  
listings によるコード表示の設定。  
背景色、行番号、キーワード色、枠線などを統一。

## 📄 main.tex の基本構造

```latex
\documentclass[10pt,twoside]{book}

\input{preamble/packages}
\input{preamble/fonts}
\input{preamble/colors}
\input{preamble/layout}
\input{preamble/header-footer}
\input{preamble/chapter-style}
\input{preamble/section-style}
\input{preamble/column-style}
\input{preamble/code-style}

\begin{document}

\tableofcontents

\chapter{はじめに}
本文…

\section{セクションタイトル}
本文…

\plainsection{番号なしセクション}
本文…

\end{document}
```

### 📝 番号なしセクションについて
標準の \section* はテンプレートのデザインと互換性がないため、
番号なしセクションには \plainsection を使用します。

``` latex
\plainsection{注意事項}
```

## 📖 PDF ビューワの見開き設定
Adobe Reader を使用する場合は、以下の設定を推奨します。
- 見開きページ表示
- 表紙を見開きに表示

これにより、左ページ＝偶数、右ページ＝奇数の正しい製本順で表示されます。

## 🎨 表紙について
本テンプレートでは \maketitle を使用しません。
表紙は後で別 PDF として作成する方針です。

## ⚠ 注意点
- \section* は使用しないでください（デザインが崩れます）
- 章扉は自動的にページ番号なしになります
- レイアウトは A5 判に最適化されています
- layoutA4report.texを読み込むことで、A4レポート形式での出力も可能です。
    - 詳細は、A4reportFoemat.pdfを参照ください。
