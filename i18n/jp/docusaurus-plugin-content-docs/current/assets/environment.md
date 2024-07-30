---
sidebar_position: 40
---

# 環境

「3D背景」とも呼ばれる環境は、キャラクターの背後に表示される3Dシーンです。[Mod SDK](../modding/mod-sdk)を使用して独自の環境をインポートできます。

![](/doc-img/jp-environment-2.png)
<p class="img-desc">温泉の環境</p>

## Steamワークショップ

Warudoソフト内蔵の環境に加えて、WarudoのSteamワークショップから公式およびコミュニティ制作の環境をダウンロードすることができます。**[ディスカバー]** タブをクリックして、**[環境]** カテゴリを選択します。

![](/doc-img/jp-environment-1.png)
<p class="img-desc">Steamワークショップから好みの環境を選べます！</p>

## 設定

環境を設定するには、環境のモデルとして**ソース**を選択するだけです。

![](/doc-img/jp-environment-3.png)

:::tip
[**指向性ライト**](lights)アセットを使用してキャラクターの照明をより細かく制御できるように、**[Allow Lights To Affect Characters]（キャラクターへのライトの影響を許可）** をオフにすることをおすすめします。
:::

:::tip
シーンの雰囲気を構築するには、環境の設定はほんの始まりに過ぎません。[カメラ](camera)アセットが提供するポストプロセス効果を検討するべきです。また、Universal Render Pipeline（URP）を使用しているWarudo Proユーザーの場合は、[ポストプロセシングボリューム](ppv)および[NiloToonボリューム](nilotoon-volume)アセットも検討するとよいでしょう。
:::

:::caution
環境を移動および回転させることは可能ですが、この操作は推奨されません。代わりに、キャラクターを移動および回転させるべきです。これは、ほとんどの環境が移動や回転を前提に設計されておらず、そのような操作を行うと環境に視覚的な不具合が発生する可能性があるためです。
:::

## 環境設定を上書き

環境設定（**アンビエントライトソース**、**環境反射強度**など）を上書きすることができます。ただし、これらの設定がすべての環境でサポートされているわけではないことに注意してください。例えば、環境がベイク処理された照明を使用している場合、**アンビエントライトソース**は無視されます。

<AuthorBar authors={{
  creators: [
    {name: 'HakuyaTira', github: 'TigerHix'},
  ],
  translators: [
    {name: '星影月夜', github: 'unsolublesugar'},
  ],
}} />