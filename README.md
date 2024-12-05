# menuScraper
Bot telegram che scarica i menù dei due ristoranti che servono la facoltà di Informatica ad UniTo e li manda come messaggio agli studenti iscritti.

## Preparazione

### secrets
Creare un file `secrets.json` con la seguente struttura:
```json
{
  "token": "",
  "db_username":"",
  "db_password":"",
  "db_host":"",
  "database":""
}
```
### cookies
Creare un file `cookies.json` con la seguente struttura:
```json
[
  {
        "Host raw": "https://.facebook.com/",
        "Name raw": "datr",
        "Path raw": "/",
        ....
  },
  {
        "Host raw": "https://.facebook.com/",
        "Name raw": "c_user",
        "Path raw": "/",
        ....
  },
  {
        "Host raw": "https://.facebook.com/",
        "Name raw": "xs",
        "Path raw": "/",
        ....
  }
]
```
credo che bastino solo questi tre cookie `xs`, `c_user` e `datr`, ma non nel dubbio usare una estensione per il browser che permetta di esportare tutti i cookie di un sito in un file json.
[cookie-quick-manager](https://github.com/ysard/cookie-quick-manager) disponibile per firefox e chrome.

### database
modificare il metodo main del file `bot.py` specificando all'interno del comando create_engine il database che si vuole usare. 
Io ho utilizzato Mariadb, quindi mysql+pymysql

## Docker 
Il file `docker-compose.yml` crea due container: il bot in se ed il database a cui il bot si collegherà.

volendo si può modificare per andare ad utilizzare il database che si preferisce, basta che questo sia compatibile con SQLAlchemy e che ci si ricordi di specificare all'interno del comando create_engine nel file `bot.py` il database che si vuole usare.
