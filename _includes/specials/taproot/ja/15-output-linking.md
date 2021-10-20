{% auto_anchor %}

Taprootがアクティベートされると、ユーザーはP2TRアウトプットへの支払いを受け入れます。
その後、ユーザーはそのアウトプットを使用します。場合によっては、
P2TR以外のアウトプットに支払いをして、P2TRのお釣り用アウトプットを使って自分自身にお釣りを返すこともあります。

{:.center}
![Example transaction P2TR -> {P2WPKH, P2TR}](/img/posts/2021-10-p2tr-to-p2tr_p2wpkh.png)

このようなトランザクションを観察している専門家やアルゴリズムは、
P2TRアウトプットがユーザー自身のお釣り用のアウトプットであり、
もう一方のアウトプットが支払い用のアウトプットであると合理的に推測することができます。
これが真実であるとは限りませんが、最も可能性の高い説明です。

ウォレットがP2TRに移行する間、このように一時的にプライバシーが低下する可能性があるため、
Taprootの[プライバシー上の利点][p4tr benefits]を無視すべきだと主張する人もいます。
多くの専門家は、それは不当な過剰反応である[としています][coindesk experts]。
私たちもそれに同意し、さらにいくつかの反論をしたいと思います:

- **<!--other-metadata-->他のメタデータ:** トランザクションには、どのアウトプットがお釣りで、
  どのアウトプットが支払いかを明らかにする、その他のメタデータが含まれている場合があります。
  最も気になるのは、現在[アドレスを再利用している][topic output linking]アウトプットが大きな割合を占めており、
  これらのトランザクションに関わる送信者と受信者の両方のプライバシーが著しく低下していることです。
  これらの問題が続く限り、ベストプラクティスを実装しているウォレットやサービスのユーザーのプライバシーを
  大幅に改善しないのは愚かなことだと思います。

- **<!--output-script-matching-->Output Scriptのマッチング:** Bitcoin Coreの内蔵ウォレットでは、
  支払いのアウトプットタイプのいずれかがsegwitでもある場合、
  デフォルトで[segwitのお釣り用アウトプット][bitcoin core #12119]を使用します。
  それ以外の場合、デフォルトのお釣り用アドレスタイプを使用します。
  例えば、P2PKHのアウトプットへの支払い時には、P2PKHのお釣り用アウトプットが使用され、
  P2WPKHアウトプットに対しては、P2WPKHのお釣りが使用されます。
  [ニュースレター #155][news155 bcc22154]に記載されているように、Taprootのアクティベート後、
  Bitcoin Coreは、同じトランザクション内の他のアウトプットがP2TRである場合、
  P2TRのお釣り用アウトプットを機会的に使用し始めます。
  これにより、移行期間中のお釣りの識別性の増加を最小限に抑えることができます。

- **<!--request-upgrades-->アップグレードのリクエスト:** P2TRの使用は、
  セキュリティ要件に関係なく、誰もが同じタイプのOutput Scriptを使用することができ、
  また、区別できないインプットを頻繁に使用することで、プライバシーを大幅に向上させることができるという、
  Bitcoinの歴史上初めての機会になります。
  Bitcoinのプライバシーを有意義に向上させたいのであれば、あなたが支払いをしているユーザーやサービスに、
  Taprootのサポートを提供するよう依頼することができます（また、該当する場合は、アドレスの再利用を停止することも）。
  あなたと彼らの両方がアップグレードすれば、お釣り用アウトプットの識別は難しくなり、
  Taprootの他の驚くべきプライバシー上の利点もすべて得られます。

{% include linkers/issues.md issues="12119" %}
{% endauto_anchor %}
[p4tr benefits]: /ja/preparing-for-taproot/#マルチシグの概要
[p4tr safety]: /ja/preparing-for-taproot/#なぜ待つ必要があるのか？
[coindesk experts]: https://www.coindesk.com/tech/2020/12/01/privacy-concerns-over-bitcoin-upgrade-taproot-are-a-non-issue-experts-say/
[compat bcc]: /en/compatibility/bitcoin-core/
[news155 bcc22154]: /ja/newsletters/2021/06/30/#bitcoin-core-22154