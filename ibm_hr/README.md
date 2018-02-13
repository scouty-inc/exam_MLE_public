# MLE 技術試験（モデリング編）

## はじめに
scoutyの機械学習エンジニアに求められる素質は、次の6つです。

1. 実現したいアプリケーションに対して、様々なモデルを考案し、それを素早くプロトタイピングをする。「本当にこのアルゴリズムで行けるのか？」をすぐ試す。
1. 作ったモデルをサービスに組み込むコードを書く。
1. 作ったモデルの精度を上げるために、パラメータチューニングをしたり、アンサンブルをしたり、別なモデルを試したり、新しいモデルを開発したりする。
1. 新しいモデル に関して、論文を書いたり、特許を取ったり、ブログを書いたりする形で、公表する。
1. 3に役立つような 最新手法や既存手法などに関して、リサーチやインプットを行う。
1. 1の結果を得て、アルゴリズムの要件定義を行なう。それに付随して顧客やPMと話し、アルゴリズム開発の統括を行なう。

もちろん、このすべてを1人でこなすことを期待しているわけではなく、各人が自分の得意分野を担当するイメージです。（それによって、「実装系機械学習エンジニア」「リサーチャー」「アルゴリズムマネージャ」などと変わります。）

この試験は、上記の **1** をテストする試験です。

## 問題
ファイル内の ibm\_data\_train.csv および ibm\_data\_test.csv は、[IBMが公開しているHRデータ](https://www.ibm.com/communities/analytics/watson-analytics-blog/hr-employee-attrition/)から作成されたもので、各従業員のプロファイルと、それぞれの満足度、退職年数、パフォーマンスが記録されているCSVデータです。

例えばPythonで実装する際は、各データ項目とその型は、

```python
import pandas as pd
file_path_train = './ibm_data_train.csv'
df_train  = pd.read_csv(file_path_train)

print(df_train.dtypes)
```

とすることで見ることができます。
一部の5(4)段階評価の項目の内容は、以下のようになります。

| アイテム名 | 1 | 2 | 3 | 4 | 5 |
| ------------ | ------------- | ------------- | ------------- | ------------- | ------------- |
| Education | Below College | College | Bachelor | Master | Docter |
| JobInvolvement | Low | Medium | High | Very High | - |
| JobSatisfaction | Low | Medium | High | Very High | - |
| PerformanceRating | Low | Good | Excellent | Outstanding | - |
| RelationshipSatisfaction | Low | Medium | High | Very High | - |
| WorkLifeBalance | Bad | Good | Better | Best | - |

我々は、このデータの中では TotalWorkingYears （勤務年数）に最も興味があります。この数字が他のプロファイルから予測できたら、その人の退職時期を予測できるからです。

50分間で、従業員の TotalWorkingYears 以外の情報から、 TotalWorkingYears を予測するアルゴリズムを作ってください。
そして、与えられたテストデータに対して平均二乗誤差を計算するテスト関数を作ってください。


学習は、 ibm\_data\_train.csv (1300件)、テストは ibm\_data\_test.csv  (170件) に対して行なってください。ふたつのデータ形式は全く同じです。

ライブラリやグーグル検索は、自由に使って構いません。
実装に用いる言語やツールは問いませんが、特にこだわりの無い場合は Jupyter Notebook を使って解析を行なうことを推奨しています。


## 備考
完璧なデータ解析を目指すより、まず動くものをスピーディにつくりあげてください。中にはアルゴリズムに取り入れにくい特徴もあるので、そういったものは後回しにしても構いません。
実装の後で、

* なぜその手法を選んだか
* どの特徴がTotalWorkingYearsに影響を及ぼしているか
* もし時間があったらやること（「この要素を取り入れればもっと精度が上がる」「この特徴をアルゴリズムに加えるには、このようにする」等）

といったことを可能な範囲でプレゼンしていただきます。
