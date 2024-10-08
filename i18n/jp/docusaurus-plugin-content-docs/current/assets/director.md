---
sidebar_position: 400
---

# ディレクター

:::info
この機能は[Warudo Pro](../pro)でのみ利用可能です。
:::

ディレクターアセットは、シンプルかつ強力なシネマティックカメラコントロールを提供し、ハイクオリティなライブパフォーマンスを簡単に実現できます。

![](/doc-img/en-director-1.png)
<p class="img-desc">ディレクターのビデオスイッチャー</p>

:::tip
ディレクターは、受賞歴のあるプロシージャルカメラシステムであるUnityの[Cinemachine](https://unity.com/unity/features/editor/art-and-design/cinemachine)に基づいています。Cinemachineのユーザーであれば、ほとんどのバーチャルカメラの概念に馴染みがあるでしょう。
:::

## 設定 {#setup}

Proライセンスには、事前に設定されたディレクターアセットを含むサンプルシーンが含まれています。このサンプルシーンから始めて、ディレクターの動作を体感することをおすすめします。その後、**[アセットをエクスポート]** ボタンを使用してディレクターアセットをJSON文字列にエクスポートし、**[アセットをインポート]** ボタンを使用して独自のシーンにインポートできます。

ディレクターアセットは[カメラ](./camera)アセットを制御し、アニメーションを付けます。**[Camera]** ドロップダウンで制御したいカメラを選択できます。カメラの制御をディレクターとユーザー（例：自由観察、オービットキャラクター）間で切り替えるには、Tabキーの上にある **`** キーを押します。

**[Virtual Cameras]** リストには、ディレクターが切り替えることができるバーチャルカメラの一覧が表示されます。バーチャルカメラは、ディレクターがそれに切り替えたときにカメラの位置、向き、およびアニメーションを決定します。バーチャルカメラの名前の横に表示されているホットキーを押して、そのバーチャルカメラに切り替えることができます。また、**[Live Camera]** オプションを直接設定することもできます。

![](/doc-img/en-director-2.png)
<p class="img-desc">ホットキーを押してバーチャルカメラに切り替えます</p>

デフォルトでは、 **[Switcher]** が有効になっています。スイッチャーのUIは、バーチャルカメラのグリッドをプレビューし、それらを切り替えるための直感的な方法を提供します。**左右矢印**キーを使用して前のページ/次のページに移動し、**マウスの左ボタン**を使用して選択したバーチャルカメラに切り替えることができます。もちろん、ホットキーを使用してバーチャルカメラを切り替えることもできます。

:::tip
スイッチャーを有効にすると、パフォーマンスに影響を与える可能性があります。FPSが低下している場合は、 **Grid Size**と **Update Rate**を減らすか、スイッチャーを完全に無効にしてみてください。
:::

## Virtual Cameras

新しいバーチャルカメラを追加するには、**[Virtual Cameras]** リストの下にある **+** ボタンをクリックするだけです。その後、バーチャルカメラを自由に設定できます。

### Blend Animation

このオプションは、ディレクターがこのバーチャルカメラに切り替えるときにカメラがどのようにアニメーションされるかを決定します。デフォルトでは、カメラはバーチャルカメラに**カット**されます。つまり、カメラが瞬時にバーチャルカメラの位置と向きに移動します。代わりに、**EaseIn**や**EaseOut**などの**Default Blend**を選択して、バーチャルカメラにスムーズに遷移させることもできます。

### Camera Animation

バーチャルカメラにアニメーションを追加するには、まず **Camera Animation** を有効にし、**Single Duration**を指定します。その後、チェックボックスがオンになっているこのバーチャルカメラのすべてのオプションが、指定された期間でアニメーションされます。

例えば、カメラの**Field Of View（視野角）**を35から60にアニメーションさせたい場合、まず**Field Of View**の横のチェックボックスをオンにします。そして、**Offset**フィールドにデフォルト値からのオフセットを指定します。この場合、オフセットは25です。

![](/doc-img/en-director-3.png)
<p class="img-desc">視野角を35から60にアニメーションさせる</p>

カメラの**Follow Offset**や**Look At Offset**など、バーチャルカメラ内のほぼすべてのオプションをアニメーションさせることができます。詳細については、以下のセクションを参照してください。

アニメーションの **Loop Type** も設定できます。**Play Once** はアニメーションが一度だけ再生されることを意味します。 **Repeat** はアニメーションが無限にループすることを意味します。**Back And Forth** はアニメーションがループ再生されますが、毎回終わりに達するとアニメーションの方向が反転します（上記の例ではと、視野角が35から60にアニメーションされ、その後60から35、再び35から60にアニメーションします）。

最後に、**Auto Switch Camera On Animation End**を有効にして複数のカメラアニメーションを連結することができます。これにより、次々と再生されるカメラアニメーションのシーケンスを作成することができます。

### Field Of View

カメラの視野角（度数単位）。視野角が小さいほど視野が狭くなり、大きいほど視野が広くなります。

:::tip
実際のコンサートでよく使われるレンズを模して、コンサートシーンでは通常低い値（\<35）に設定します。
:::

### Position

カメラの位置。

* **Manual**モードでは、位置を直接指定できます。
* **Follow Target** モードでは、カメラを**Target**と同じ位置に配置します。ターゲットはキャラクター、道具、またはアンカーに設定できます。**Damping**オプションを使用してカメラの動きをスムーズにすることができます。
* **Transposer** モードでは、カメラを**Target**と同じ位置に配置しますが、**Follow Offset**オプションで指定されたオフセットがあります。 **Binding Mode**も設定できます（ドキュメントは[こちら](https://docs.unity.cn/Packages/com.unity.cinemachine@2.8/manual/CinemachineBindingModes.html)）。各平行移動/回転軸に対してDampingオプションが利用可能です。
* **Orbital Transposer**モードは **Transposer**モードに似ていますが、カメラはターゲットの周りの軌道上にあり、**Angular Offset**で指定された位置に配置されます。

実際には、**Manual**、**Transposer**、および**Orbital Transposer**が最もよく使用されるPositionモードです。

:::caution
よくある間違いは、**Target**をキャラクターのボーン（例：頭）に設定することです。キャラクターが動かないときは問題ないように見えますが、キャラクターが動くとカメラがキャラクターと一緒に激しく動き、非常に揺れるカメラになってしまいます！これを避けるには、**Target Character Mode**を**Root Position**に設定し、**Fixed Rotation**を有効にします。あるいは、ほとんどの場合で **Manual** Positionモードを使用したほうが良いでしょう！
:::

### Orientation

カメラの向き。

* **Manual** モードでは、向きを直接指定できます。
* **Follow Target** モードでは、カメラを**Target**と同じ向きに配置します。ターゲットはキャラクター、道具、またはアンカーに設定できます。**Damping**オプションを使用してカメラの動きをスムーズにすることができます。
* **First Person** モードでは、マウスを使用して周囲を見回すことができます。**Set Initial Rotation**ボタンをクリックして、次回シーンが読み込まれたときにカメラが現在の向きから開始するように設定します。
  :::caution
  **First Person** Orientationモードは現在、**Switcher** UIと互換性がありません。**First Person** Orientationモードを使用するには、**Switcher**を無効にする必要があります。
  :::
* **Hard Look At Character** モードでは、カメラが常に**Target**を見つめるように強制されます。
* **Composer** モードでは、カメラを**Target**に向けて回転させますが、**Look At Offset**オプションで指定されたオフセットがあります。さらに、**Screen X**と**Screen Y**を変更して、ターゲットを画面の中央以外の位置に配置することができます。
  - **Composition** パラメータを使用して、カメラ構成の**Dead Zone**、**Soft Zone**、および**Bias**を調整し、ターゲットがわずかに動いたときにカメラがあまり動かないようにします。
  - **Lookahead** パラメータを使用して、カメラがターゲットの動きを予測できるようにします。
  :::tip
  Composerの視覚的な説明については、[このブログ記事](https://blogs.unity3d.com/2019/07/24/understanding-cinemachine-fundamentals/)を参照してください。
  :::

実際には、**Manual**と**Composerが**最もよく使用されるOrientationモードです。

:::caution
よくある間違いは、**Composer**モードで**Dead Zone**と**Soft Zone**を設定し忘れることです。これにより、ターゲットがわずかに動いたときにカメラが過剰に動き、非常に揺れるカメラになってしまいます！カメラが正しい位置にあることを確認してから、**Dead Zone**と**Soft Zone**の設定を行なってください。
:::

:::tip
**Position**と**Orientation**モードの両方を**Manual**に設定した固定カメラは、思った以上に便利です。リスナーの認知負荷を軽減し、映像酔いを防ぐことができます。**Handheld Movement**（下記参照）を追加して、固定カメラをより自然に見せることができます。
:::

### Position/Orientation Offset

カメラのデフォルトの位置/向きからのオフセットです。カメラの位置/向きを現在の位置/向きからアニメーションさせたい場合に便利です。

### Handheld Movement

カメラを人が持っているような動きをシミュレートします。カメラの動きにわずかな揺れが加わります。**Intensity**と**Speed**を調整して、揺れの強さと速度を制御できます。

### Collision Detection

カメラの衝突検出を有効にし、カメラが壁や他のコライダーを通り抜けないようにします。**Camera Collision Radius**と**Damping**を調整して、カメラのサイズと衝突検出の強さを制御できます。

## Global Offsets

**Global Offsets**セクションでは、**Camera Animation Speed**、**Field Of View**、**Position**、**Orientation**、**Zoom**など、すべてのバーチャルカメラに対してグローバルオフセットを指定できます。これには、どのバーチャルカメラが現在アクティブであるかに関係なく、オーディオボリュームに基づいてズームイン/ズームアウトなどの効果を実装するのに特に便利です。

<AuthorBar authors={{
  creators: [
    {name: 'HakuyaTira', github: 'TigerHix'},
  ],
  translators: [
    {name: '星影月夜', github: 'unsolublesugar'},
  ],
}} />
