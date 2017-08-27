% プログラミングの練習
% ka
% 2017-08-27

# Author

ka

[![Gravatar](https://gravatar.com/avatar/884be098693425b409d25aaec5091de8?s=150)](https://gravatar.com/ka000)

Website: [kaosfield](http://www.kaosfield.net)

Twitter: [ka](https://twitter.com/ka_)

GitHub: [kaosf](https://github.com/kaosf)

# License

[![CC BY-NC-SA 4.0](https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-nc-sa/4.0/)

Copyright (C) 2017 ka

# このページとリポジトリ

[https://kaosf.github.io/20170827-tokushimarb-slide](https://kaosf.github.io/20170827-tokushimarb-slide)

Repository: [kaosf/20170827-tokushimarb-slide - GitHub](https://github.com/kaosf/20170827-tokushimarb-slide)

# 注意

最後から読むとネタバレします

最初から読んでいくことをオススメします

# 1から10まで表示

出力

```
1
2
3
...
10
```

# 考え方

## その1

<ol>
<li>1を変数に代入</li>
<li>変数の値を表示する</li>
<li>変数に現在の変数の値+1を代入</li>
<li>変数の値が10より大きければ終了</li>
<li>1に戻る</li>
</ol>

# 考え方

## その2

1から10までの配列(リスト，範囲という感じ)を用意する

その要素を全て表示する

# 1から10まで表示 Ruby版

答え(あくまで一例です)

```ruby
(1..10).each do |e|
  puts e
end
```

# 1から10まで表示 JavaScript版

答え(あくまで一例です)

```javascript
for (var i = 1; i <= 10; i++) {
  console.log(i);
}
```

# ここまではまだまだ簡単

この先はRuby版のコードのみを示します

JavaScript版やその他の言語版を作れた人はコード下さい

スライドに追加します

# 1から19までの奇数を表示

出力

```
1
3
5
...
19
```

# 1から19までの奇数を表示

答え

```ruby
(1..10).map { |e| 2 * e - 1 }.each do |e|
  puts e
end
```

# 1から19までの奇数の和を表示

出力

```
100
```

※

$$1 + 3 + 5 + \ldots + 19 = 100$$

# 1から19までの奇数の和を表示

```ruby
s = (1..10).map { |e| 2 * e - 1 }.reduce(0) { |a, e| a + e }
puts s
```

# 1から19までの奇数の和を表示

※reduceを使わない版

```ruby
s = 0
(1..10).map { |e| 2 * e - 1 }.each do |e|
  s += e
end
puts s
```

# 1から19までの奇数の和を表示

※もっと簡単版(練習にはならない)

```ruby
s = (1..10).map { |e| 2 * e - 1 }.sum
puts s
```

# 1から39までの奇数を2つずつ表示

```
1 3
5 7
9 11
...
33 35
37 39
```

# 1から39までの奇数を2つずつ表示

```ruby
(1..10).map { |e| 4 * e - 3 }.each do |e|
  puts("#{e} #{e + 2}")
end
```

# 1から39までの奇数の2つずつの積を表示

```
3
35
...
1155
1443
```

※
$$1 \times 3 = 3$$
$$5 \times 7 = 35$$
$$33 \times 35 = 1155$$
$$37 \times 39 = 1443$$

# 1から39までの奇数の2つずつの積を表示

```ruby
(1..10).map { |e| (4 * e - 3) * (4 * e - 1) }.each do |e|
  puts e
end
```

# 1から39までの奇数の2つずつの積の逆数を表示

```
0.3333333333333333
0.02857142857142857
...
0.0008658008658008658
0.000693000693000693
```

※

$$\frac{1}{1 \times 3} \fallingdotseq 0.333$$
$$\frac{1}{5 \times 7} \fallingdotseq 0.0286$$
$$\frac{1}{33 \times 35} \fallingdotseq 0.000866$$
$$\frac{1}{37 \times 39} \fallingdotseq 0.000693$$

# 1から39までの奇数の2つずつの積の逆数を表示

```ruby
(1..10).map { |e| 1.0 / ((4 * e - 3) * (4 * e - 1)) }.each do |e|
  puts e
end
```

# 1から39までの奇数の2つずつの積の逆数の和を表示

出力

```
0.38645297583347976
```

※

$$\frac{1}{1 \times 3} + \frac{1}{5 \times 7} + \ldots + \frac{1}{33 \times 35} + \frac{1}{37 \times 39} \fallingdotseq 0.386$$

# 1から39までの奇数の2つずつの積の逆数の和を表示

```ruby
s = (1..10).map { |e| 1.0 / ((4 * e - 3) * (4 * e - 1)) }.reduce(0.0) { |a, e| a + e }
puts s
```

# 1から399までの奇数の2つずつの積の逆数の和を表示

出力

```
0.3920740856048518
```

これまで 10 個の「2つずつ」を扱っていたが

次は 100 個の「2つずつ」を扱うことにする

プログラムの変更箇所がどこになるのか？すぐに分かるでしょう

# 1から399までの奇数の2つずつの積の逆数の和を表示

```ruby
s = (1..100).map { |e| 1.0 / ((4 * e - 3) * (4 * e - 1)) }.reduce(0.0) { |a, e| a + e }
puts s
```

# …一体何をしているのでしょうか？

実は意味のある計算をしています

# 唐突に8を掛ける

10個のバージョンと100個のバージョンのそれぞれの答えに8を掛けてみる

```ruby
s = (1..10).map { |e| 1.0 / ((4 * e - 3) * (4 * e - 1)) }.reduce(0.0) { |a, e| a + e }
s *= 8
puts s

s = (1..100).map { |e| 1.0 / ((4 * e - 3) * (4 * e - 1)) }.reduce(0.0) { |a, e| a + e }
s *= 8
puts s
```

# 察しがついたでしょうか？

# 1000個にしてみる

```ruby
s = (1..1000).map { |e| 1.0 / ((4 * e - 3) * (4 * e - 1)) }.reduce(0.0) { |a, e| a + e }
s *= 8
puts s
```

# 10000個にしてみる

```ruby
s = (1..10000).map { |e| 1.0 / ((4 * e - 3) * (4 * e - 1)) }.reduce(0.0) { |a, e| a + e }
s *= 8
puts s
```

# もう分かりましたね？

次のページから種明かしです

# 種明かし

実は

$$\frac{1}{1 \times 3} + \frac{1}{5 \times 7} + \frac{1}{9 \times 11} + \ldots + \frac{1}{(4n - 3) \times (4n - 1)} + \ldots = \frac{\pi}{8}$$

無限にこの規則で足し算していくと $\frac{\pi}{8}$ に収束します

# 種明かし

この計算は $\tan^{-1} x$ のマクローリン展開で $x$ に $1$ を代入した結果と関係があります

マクローリン展開された形は

$$\tan^{-1} x = \frac{x}{1} - \frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \ldots$$

となります

# 種明かし

$x$ が $1$ のときは分子は常に $1$ なのでこれを2項ずつまとめると

$$\tan^{-1} 1 = \frac{1 (3 - 1)}{1 \times 3} + \frac{1 (7 - 5)}{5 \times 7} + \ldots$$

$$\tan^{-1} 1 = \frac{1 \times 2}{1 \times 3} + \frac{1 \times 2}{5 \times 7} + \ldots$$

$$\frac{1}{2} \tan^{-1} 1 = \frac{1}{1 \times 3} + \frac{1}{5 \times 7} + \ldots$$

# 種明かし

$\tan^{-1}$ は $\tan$ の逆関数なので $\tan \frac{\pi}{4} = 1$ (直角二等辺三角形) より

$$\tan^{-1} 1 = \frac{\pi}{4}$$

※$\tan$の計算は直角三角形の直角を挟む二辺の長さの比です

※$\frac{\pi}{4}$ は角度45度の別の表現です この表現方法でなければマクローリン展開が扱えません

# 種明かし

$$\tan^{-1} 1 = \frac{\pi}{4}$$

なので

$$\frac{1}{2} \tan^{-1} 1 = \frac{1}{1 \times 3} + \frac{1}{5 \times 7} + \ldots = \frac{1}{2} \times \frac{\pi}{4}$$

となり全体に8を掛ける(唐突に8を掛けたのはそういう意味です)と

$$4 \tan^{-1} 1 = 8 \times (\frac{1}{1 \times 3} + \frac{1}{5 \times 7} + \ldots) = \pi$$

# この先

ではこのまま1億個，1兆個…と続けていけばもっといい近似値が得られるか？

…と考えるところですが実はこの計算は収束が非常に遅いのでなかなか正確な桁数は増えません

あとそもそも時間が掛かりすぎます

それと計算すればするほど浮動小数点の計算の誤差が蓄積していき実際の値から外れていく…はずです(手元では未確認ですが)

もっと収束の早い計算はもっと複雑なのでプログラミングの練習としては扱いません

趣味でやってみて下さい

# おしまい
