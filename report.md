レポート内容
変更点
startメソッドの出力を
"logger.info 'Trema started'"から、
"logger.info "Hi! from #{self.class}""へ変更した。
self.classによって、当該メソッドを呼び出したクラスのオブジェクトを取得することができる。
そして、self.classで表される文字列を出力できるように、出力文をダブルクォーテーション"に変更し、
変数を文字列中に展開できるように#{}でself.classを囲んだ。
以下に、変更したソースコードを記載する。

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