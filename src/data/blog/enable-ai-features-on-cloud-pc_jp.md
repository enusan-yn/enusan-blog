---
author: Sanghyeon Yeo
pubDatetime: 2026-01-20T00:00:00Z
title: AI対応クラウドPCを設定しよ
slug: enable-ai-features-on-cloud-pc-jp
featured: false
draft: false
tags:
  - intune
  - windows365
  - cloudpc
  - ai
description:
  AI対応クライドPCを設定する方法を説明します。
---

# 紹介
Microsoftは以前２０２４年にCopilot+ PCを発表したあと続いてWindowsにAI機能を統合しています。Copilot+ PCにはAI計算を効率的に勝利するNPUが搭載されており、AIを早くて効率的に作動することができます。そのため、Windows 11に追加されたAI機能の中にNPUを必要とする機能がいくつかあります。

Windows 365のAI対応クラウドPCはMicrosoft CloudにNPUのようにAI処理部が追加され、Copilot+ PCのようのNPUを必要するWindowsのAI機能を利用できるクラウドPCです。AI対応クラウドPCを利用することで、どんな種類のデバイスからでもAI機能が使えるPCを利用できます。

現在はCopilot+ PCから利用できる機能の中一部の機能のみ利用可能です。

- 改良されたWindows Search [Find files fast with improved Windows search](https://www.microsoft.com/en-us/windows/learning-center/find-files-fast-with-improved-search)
- クリックして実行 [クリックして実行: 画面に表示されている情報をさらに活用する](https://learn.microsoft.com/ja-jp/windows/apps/develop/windows-integration/click-to-do)

# 要件
AI対応クラウドPCは現在フロンティアプレヴューとして提供されているため、Copilotフロンティアプログラムに参加しているテナントのみ利用が可能です。

- さいて8vCPU、32GB RAM、256GB　ストレッジSKUのWindows 365 Enterprise。
- Windows Insider Programに参加が必須です。
- Windows OSのビルドが26100.6584(24H2)または26200.6584(25H2)以上が必要があります。
- PowerShellのExecutionPolicyはRemotedSignedで設定する必要があります。
- Enable features introduced via service that are off by default policyポリシーを有効にする必要があります。

# 設定方法
Intune管理センターでクラウドPCの構成を作成割り当ててAI対応クラウドPCを設定することができます。



1. Intune管理センターでデバイス＞Windows 365>設定>作成＞クラウドPCの構成の順にクリックします。
  
![Image](@/assets/images/enable-ai-features-on-cloud-pc/01_JP.png)
  
2. 構成設定段階でAI-enabled featuresを有効にするで設定します。   
  
![Image](@/assets/images/enable-ai-features-on-cloud-pc/02_JP.png)
  
3. クラウドPCの構成を割り当てるユーザーグループを選択します。
  
![Image](@/assets/images/enable-ai-features-on-cloud-pc/03_JP.png)
  
4. 設定した内容を確認した後、作成ボタンをクリックします。
  
![Image](@/assets/images/enable-ai-features-on-cloud-pc/04_JP.png)

# AI対応クラウドPCになってるか確認する方法
クラウドPCの構成がユーザーに割り当てた後クラウドPCに必要なバックグラウンド作業が進むまでは最大４８時間がかかります。バックグラウンド作業が終わったらクラウドPCでWindowsアップデートの項目がこれ以上表示されなきなるまで、繰り返して更新した後再起動したらAI対応クラウドPCになったことを確認できます。

## Windows App
AI対応クラウドPCはWindowsアプリでAI-Enabledとしたタグがついて表示されます。
  
![Image](@/assets/images/enable-ai-features-on-cloud-pc/WindowsApp.png)

## Windowsテスクバー
Windowsタスクバーにある検索ボックスに虹色のエフェクトが表示されます。
  
![Image](@/assets/images/enable-ai-features-on-cloud-pc/taskbar.png)

## Intune 管理センター
概要ページで、AIが有効項目がはいと表示されます。
  
![Image](@/assets/images/enable-ai-features-on-cloud-pc/intuneconsole_jp.png)

# Read more
[Experience next-gen productivity with Windows 365 AI-enabled Cloud PCs](https://techcommunity.microsoft.com/blog/windows-itpro-blog/experience-next-gen-productivity-with-windows-365-ai-enabled-cloud-pcs/4467875)
  
[AI-enabled Cloud PC (Frontier Preview)](https://learn.microsoft.com/en-us/windows-365/enterprise/ai-enabled-cloud-pcs)