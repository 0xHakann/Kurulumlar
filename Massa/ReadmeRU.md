<p style="font-size:14px" align="right">
 100$ Бесплатный VPS на 2 Месяца <br>
 <a target="_blank" href="https://www.digitalocean.com/?refcode=410c988c8b3e&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge"><img src="https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%201.svg" alt="DigitalOcean Referral Badge" /></a></br>
 <a href="https://t.me/nodeistt" target="_blank"><img src="https://github.com/Nodeist/Testnet_Kurulumlar/blob/fee87fe32609c1704206721b9fb16e4c5de75a96/telegramlogo.png" width="30"/></a><br>Присоединяйтесь к Telegram<br>
<a href="https://nodeist.site/" target="_blank"><img src="https://raw.githubusercontent.com/Nodeist/Testnet_Kurulumlar/main/logo.png" width="30"/></a><br> Посетите наш сайт
</p>


### Минимальные аппаратные требования
  - 3x ЦП; чем выше тактовая частота, тем лучше
  - 4 ГБ ОЗУ
  - 100 ГБ Диск
  
  
### Советы
   - Вы наберете максимальное количество баллов, если запустите свой узел дома или в месте, где другие узлы Massa не заняты.
   - Если вы используете общий сервер (VPS), использование Интернета может привести к продаже роликов.

## Автоматическая установка с помощью одного скрипта
Вы можете настроить узел defund за считанные минуты, используя приведенный ниже автоматизированный скрипт.

```
wget -O Massa.sh https://raw.githubusercontent.com/Nodeist/Kurulumlar/main/Massa/Massa.sh && chmod +x Massa.sh && ./Massa.sh
```

## Действия после установки

Создать экран
```
screen -S massa
```


Запустить узел. Установите пароль там, где написано «ПАРОЛЬ».
```
cd massa/massa-node

RUST_BACKTRACE=full cargo run --release -- -p ПАРОЛЬ |& tee logs.txt
```


Создайте новое окно в Screen.
```
CTRL + A + C 
```


Запустите клиент. Установите пароль там, где написано «ПАРОЛЬ».
```
cd massa/massa-client/

cargo run --release -- -p ПАРОЛЬ
```
*Логически мы запускаем узел в одном окне и клиент в другом окне.*



Перейдите в окно, где запущен клиент, и создайте кошелек. Сохраните ключи, указанные в выводе.
```
wallet_generate_secret_key
```


Проверьте кошелек, резервный адрес кошелька и секретный ключ.
```
wallet_info
```


Вставьте адрес своего кошелька в канал testnet-faucet на сервере Discord Massa.
Проверьте свой баланс. Это должно быть «Final Balance 100».
```
wallet_info
```


Если все правильно создайте ролл. Отредактируйте часть «WALLETADDRESS».
```
buy_rolls WALLETADDRESS 1 0
```


Добавьте свой узел в сеть. В части «секретный ключ» напишите секретный ключ, резервную копию которого мы только что создали, введя информацию о кошельке.
```
node_add_staking_secret_keys секретныйключ

#образец
#node_add_staking_secret_keys qwoieq123981239asdasd
```


Присоединяйтесь к дискорд-серверу Massa. Нажмите на смайлик 👍 в канале testnet-rewards-registration или напишите что-нибудь в канале.
Бот отправит вам личное сообщение, и вы получите свой идентификатор раздора из этого сообщения.

![Nodeist](https://i.hizliresim.com/7w3sntd.png)



Узнав идентификатор Discord, перейдите на экран клиента вашей ноды и запустите код ниже.
Отредактируйте разделы «walletaddress» и «discordid».

```
node_testnet_rewards_program_ownership_proof walletaddress discordid
```

В ответ вы получите длинный код. скопируйте этот код и отправьте его массовому боту, который только что отправил вам личное сообщение в дискорде.
Затем отправьте IP-адрес вашего сервера тому же массовому боту.



Проверьте свой кошелек через несколько часов.
```
wallet_info
```

Если есть вывод, как на картинке ниже, вы готовы.

![Nodeist](https://i.hizliresim.com/tc4s31r.png)



### Полезная информация
Чтобы выйти из экрана:
```
ctrl+a+d
```

Чтобы войти на экран:
```
screen -r massa
```

Чтобы перемещаться между окнами узла и клиента на экране:
```
ctrl+a+p

#альтернативный ctrl+a+a
```

Вы отключились от сервера и снова подключились. Вы хотите войти в экран, но на экране уже отображается «Прикреплено».
В этом случае вам нужно сначала «Отсоединить» ваш сервер. Для этого:
```
screen -d massa
```

Это все!
