[![Typing SVG](https://readme-typing-svg.herokuapp.com?color=%2336BCF7&lines=LayerZero+:+tx_checker)](https://git.io/typing-svg)

Скрипт парсит все транзакции в 7 чейнах, ищет совпадения по контракту из модулей (ниже) и выписывает в csv файл результат : кол-во транзакций, дата первой и последней транзакции, объем в eth и объем в erc20 (стейблы).

1. testnet bridge : 
- arbitrum => goerli (eth) 
- optimism => goerli (eth) 
2. stargate : 
- arbitrum => chain (eth / usdc / usdt)
- optimism => chain (eth / usdc)
- polygon => chain (usdc / usdt)
- fantom => chain (usdc)
- ethereum => chain (eth / usdc / usdt)
3. woofi :
- arbitrum => chain (eth)
- optimism => chain (eth)
4. aptosbridge :
- arbitrum => aptos (eth)
- bsc => aptos (usdt / usdc)
5. bitcoin bridge :
- avaxc => chain (btcb)
- arbitrum => chain (btcb)
- optimism => chain (btcb)
6. holograph :
- avaxc => chain (nft)
- polygon => chain (nft)


# Настройка :

Создаем виртуальное окружение :
`python3 -m venv .venv`

Активируем :
`.venv\Scripts\activate.bat` - для Windows.
`source .venv/bin/activate` - для Linux и MacOS.

Устанавливаем библиотеки :
`pip3 install -r requirements.txt`

Накидали статью для маленьких, где все объясняется на картинках : https://teletype.in/@hodlmod.eth_kids/layerzero_tx_checker

# Настройка config.py и данных :
1. В файл `wallets.txt` выписываем адреса кошельков построчно.
2. В папке data в текстовые файлы выписываем апи ключи от сканов. Для этого нужно зарегистрироваться (ссылки ниже) и создать ключ. Одного ключа на каждый скан хватит. Ключи вписывать построчно. Увеличение кол-ва ключей лишь увеличит скорость парсинга :
- `arb_api.txt` : https://arbiscan.io/myapikey
- `avax_api.txt` : https://snowtrace.io/myapikey
- `bsc_api.txt` : https://bscscan.com/myapikey
- `opt_api.txt` : https://optimistic.etherscan.io/myapikey
- `eth_api.txt` : https://etherscan.io/myapikey
- `polygon_api.txt` : https://polygonscan.com/myapikey
- `ftm_api.txt` : https://ftmscan.com/myapikey
3. В файле `config.py` меняем значения переменных под себя :
- `MIN_VALUE_ERC20` - если объем в erc20 токенах будет меньше этого числа, кошелек выделяется.
- `MIN_VALUE_ETH` - если объем в нативных (eth) токенах будет меньше этого числа, кошелек выделяется.
- `MIN_TX_AMOUNT` - если кол-во транзакций в layerzero меньше этого числа, кошелек выделяется.
- `LAST_DATE_TX` - если последняя транзакция была сделана позже этой даты, кошелек выделяется. 
- `DAYS_AMOUNT` - если кол-во дней между первой и последней транзакцией меньше этого числа, кошелек выделяется.
- `FILE_NAME` - как назвать csv файл с результатом.
- `chains` - какие сети оставляем включенными. Если хочешь выключить сеть, закомментируй ее.

# Результат :
После выполнения скрипта, данные будут записаны в csv файл. Теперь его нужно импортировать в гугл таблицу. Как это сделать : https://topgoogle.ru/kak-importirovat-i-otkryt-csv-fajl-v-google-tablicax/

Паблик : https://t.me/hodlmodeth. [ code ] чат : https://t.me/code_hodlmodeth
