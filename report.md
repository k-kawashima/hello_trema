###課題回答
####その1
スイッチが停止すると、switch_disconnected()が呼び出される。そこで、hello_trema.rbに新たにswitch_disconnected()を定義し、その中でlogger.info "Bye #{datapath_id.to_hex}!"を追加した。これによって、スイッチ停止時に"Bye 0xabc"を表示できる。
####その2
startメソッドの出力を
"logger.info 'Trema started'"から、
"logger.info "Hi! from #{self.class}""へ変更した。
self.classによって、当該メソッドを呼び出したクラスのオブジェクトを取得することができる。
そして、self.classで表される文字列を出力できるように、出力文をダブルクォーテーション"に変更し、
変数を文字列中に展開できるように#{}でself.classを囲んだ。
####変更したソースコード

```ruby:hello_world.rb
# Hello World!
class HelloTrema < Trema::Controller
  def start(_args)
    #logger.info 'Trema started.'
    logger.info "Hi! from #{self.class}"
  end

  def switch_ready(datapath_id)
    logger.info "Hello #{datapath_id.to_hex}!"
  end

  def switch_disconnected(datapath_id)
    logger.info "Bye #{datapath_id.to_hex}!"
  end
end