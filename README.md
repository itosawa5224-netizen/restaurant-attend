# ☕️飲食店向けアテンド業務支援システム　<br>ー Restaurant Attendant Support System ー

<!--[![CI](https://github.com/yourname/project/actions/workflows/ci.yml/badge.svg)](https://github.com/yourname/project/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue.svg)](https://www.typescriptlang.org/)-->

飲食店における お客様の順番待ち受付〜席へのご案内 までの「アテンド業務」を補助するための、ホールスタッフ向け業務システムに関するポートフォリオです。

![デモのスクリーンショットやGIF](docs/images/demo.gif)

## 📖 概要

 このプロジェクトは、飲食系の繁盛店で働くホールスタッフによる使用を想定し、数あるなかでも「アテンド業務」を効率化・非属人化することで店舗全体の接客力やホスピタリティ向上へ繋げる目的で開発しました。アテンド業務に関する情報を一元管理し、スタッフ間でリアルタイムに共有できる仕組みを構築することで、繁忙時の業務負担を軽減する。


### 背景

 大学生時代に従事した飲食店でのアルバイトで、ホール業務の一環としてアテンド業務や他スタッフへの指示出しを行っていた際、以下のような<課題>に直面していた。

 繁盛する飲食店では、土日祝日のランチタイムや大型連休、年末年始などに来店客が集中する。
 その結果、受付・待機客管理・空席確認・座席決定・スタッフへの指示出しなどの業務が特定のスタッフに集中し、業務負担が増大している。

<課題>
- 紙の受付表(ウェイティングボード)による管理の煩雑さ
- 待機客の人数構成と空席状況の把握にかかる負担
- 案内順や座席決定の判断の難しさ
- 特定スタッフへの業務集中と属人化
- 待ち時間を正確に把握することが難しく、お客様への回答が困難
- 口頭による指示や情報共有の負担


### 最終的に実現したい状態
スタッフがアテンド業務に関する情報を個人の記憶や処理能力だけに頼らず把握でき、接客力やホスピタリティを発揮することに集中できる環境を実現する。
繁忙時に集中するアテンド業務の負担と、特定のスタッフに依存している業務体制を改善し、ホールスタッフが接客やホスピタリティに集中できる環境を作る

## ✨ 主な機能

- **機能1:ウェイトボード機能**: お客様にお名前・ご利用の人数構成を入力してもらう。
- **機能2:待ち時間表示機能**: (説明)
- **機能3:席確保機能**: (説明)
- **機能4:バッシング席共有機能**: (説明)

## 🛠 技術スタック

| カテゴリ | 技術 |
|:--|:--|
| フロントエンド | HTML / CSS / JavaScript / React ~~Next.js 15 / React 19 / TypeScript~~ |
| バックエンド | Java / Python / FastAPI ~~Node.js / Hono~~ |
| データベース | MySQL ~~PostgreSQL / Prisma~~ |
| 開発環境 | VS Code / Git / GitHub |
| インフラ | AWS ~~Vercel / Docker~~ |
| 設計・管理 | Mermaid / Figma |
| CI/CD | ? ~~GitHub Actions~~ |
| テスト | ? ~~Vitest / Playwright~~ |
