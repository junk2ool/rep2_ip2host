# rep2_ip2host

rep2(open774版)で名前欄にIPアドレスがあれば逆引きをしてホスト名に書き換えるもの。  
非同期でホスト名の逆引きをして書き換えるのでスレが表示されてから書き変わるまでラグがあります。  
HTML5のWeb Storageを使ってブラウザ側に逆引き結果をキャッシュをするようにしてあるので2回目以降キャッシュにあれば少し早いです。  
Web Storage対応のブラウザでない場合はrep2サーバーの/p2-php/data/tmp/にキャッシュファイルを作ります。  
また、逆引きしたホスト名にrep2の名前欄のあぼーん処理をかけて該当すれば透明あぼーんします。  
逆引きはrep2サーバー側で行い、書き換えはブラウザ側のjQueryで動的に行っているためhtmlソースには反映されません。

## Install
  * lib/ip2host.inc.php  
  * rep2/ip2host.php
 
をそれぞれの環境の/p2-phpの中に入れてください。  
その後、  
  * lib/read_footer.inc.php (PC用)
  * lib/read_footer_i.inc.php (スマホ用)

の最後方の部分に、
```php
// ここから
require P2_LIB_DIR . '/ip2host.inc.php';
// ここまで

// ====
echo '</body></html>';
```
を追記してください。

## Environment
Linux(CentOS)のPHP7+Apacheで動作確認しています。

## Note
### Cache
キャッシュはHTML5のWeb Storage(sessionStorage)を使用しています。  
そのため別タブ、ブラウザの再起動などでキャッシュは消えます。  
localStorageが使用でき、キャッシュをブラウザ側に半永久的に保持する場合はip2host.inc.phpの
```JavaScript
st = sessionStorage;
//  LocalStorageを使う場合は下記のコメントアウトを解除
//st = localStorage;
```
のコメントアウトを解除してください。  
その場合のWeb Storageのキャッシュの削除の方法は「Web Storage 削除」でぐぐれば出てきます。  
なお、キャッシュは500件を超えるとクリアするようにしています。  
500件を変更する場合はip2host.inc.phpの
```JavaScript
//  キャッシュするIPの上限数
let ip_cache_size = 500;
```
を変更してください。  

キャッシュをサーバー側のファイルに作る場合は500件を超えると古いものから10件づつ削除します。  
常にキャッシュをサーバー側のファイルで使用する場合（ブラウザ側にキャッシュを持たせたくない、複数のブラウザで使う等）はip2host.inc.phpの
```JavaScript
//  常にキャッシュをサーバー側のファイルで使用する場合は下記のコメントアウトを解除
//web_storage = 0;
```
のコメントアウトを解除してください。

### Aborn
ホスト名の名前欄でのあぼーん処理が不要な場合はip2host.inc.phpの
```JavaScript
// 名前欄のあぼーん処理を適用 する:1 しない:0
let aborn = 1;
```
を変更してください。  
ちょっと早くなると思います。

### Replace
非同期の書き換え処理には念の為タイムアウトを設定してあるので、サーバーや回線、ブラウザのスペックにより大量のレス(1-1000とか)を表示するとすべて書き変わらないことがあります。  
その場合はタイムアウトの秒数を変更するなりしてみてください。  

画面スクロール時に表示されている部分のみ随時書き換えるように変更する場合は、
```JavaScript
//  スレ表示時に一括書き換え:0 画面スクロールで書き換え:1
let scroll_replace = 0;
```
を変更してください。  

## ToDo
スマホ用ポップアップもちゃんと書き換えたい。  
(一応ポップアップさせた状態でスクロールをすると書き換わります。)

## License
[MIT License](https://mit-license.org/)

## Author
* junk2ool  
https://github.com/junk2ool/rep2_ip2host

## Reference
* rep2 expack 全部入り by open774  
https://github.com/open774/p2-php
