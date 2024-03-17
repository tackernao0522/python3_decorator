# 当デコレータコードについての説明

result = func(*args, **kwargs)の部分でadd_num(a, b)関数が実行されるとき、それはすでに@print_moreデコレータによって装飾されています。そのため、add_num(a, b)が実行される前後でprint_moreデコレータのwrapper関数内の処理が行われます。

そして、その処理が終わった後、制御が@print_infoデコレータのwrapper関数に戻り、print('end')が実行されます。

つまり、以下の順序で処理が進みます：

add_num(10, 20)が呼び出される
@print_infoデコレータが先に適用されるため、print_infoのwrapper関数が実行され、「start」が表示される
次にfunc(*args, **kwargs)が実行されるが、このfuncはすでに@print_moreデコレータによって装飾されたadd_num関数である
@print_moreデコレータのwrapper関数が実行され、関数名、引数、キーワード引数が表示される
func(*args, **kwargs)が実行され、これは実際にはadd_num(10, 20)の呼び出しである
add_num(10, 20)の結果（30）が得られ、表示される
@print_moreデコレータのwrapper関数の実行が終わり、制御が@print_infoデコレータのwrapper関数に戻る
print('end')が実行される
