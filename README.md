# SessionBridge

<p>
  <img src = "bridge.svg" alt = "logo" style = "vertical-align : middle; margin-bottom: .5rem; width : 24px; height : 24px;"/>
  <strong>SessionBridge</strong> : <strong>Pure-PHP</strong> library to convert and bridge Telegram sessions between popular client formats ( <em>Telethon , Pyrogram , Tdata , MadelineProto</em> ) and <em>LiveProto</em> ( LP )
</p>

🔥 SessionBridge focuses on compatibility, reliability, and realistic production use. It provides a unified API and CLI to read, validate, convert, and export session / auth data across different implementations of Telegram's MTProto ecosystem

---

## Key features

* Convert sessions between **Telethon** , **Pyrogram** , **MadelineProto** , **Tdata** ( Telegram Desktop ) and **LiveProto ( LP )** formats
* High-fidelity mapping of session fields where possible ( dc_id , ip , port , auth_key )
* Simple, chainable PHP API and a practical command-line interface ( CLI )

> **Note** : SessionBridge is a translator / bridge between session file formats ( or text of session ) it does **not** reimplement MTProto or perform network login for you. Use a proper client library ( MadelineProto , LiveProto , Telethon , Pyrogram ) to perform active logins and connection flows

---

## Installation

Install via Composer :

```bash
composer require taknone/sessionbridge
```

Or include directly in your project autoload

---

## Quick start

### PHP

```php
<?php

require_once 'vendor/autoload.php';

use function Tak\SessionBridge\from_madelineproto_string;

use function Tak\SessionBridge\to_liveproto_sqlite;

$sessions = from_madelineproto_string('session.madeline');

foreach($sessions as $session){
	var_dump(to_liveproto_sqlite($session));
}

?>
```

### CLI

* convert telethon.session file to LiveProto file 

```bash
php vendor/bin/sessionbridge --from telethon-sqlite --to liveproto-sqlite --session telethon.session
```

---

## Supported formats

* **Telethon** ( .session SQLite / String )
* **Pyrogram** ( .session SQLite / String )
* **MadelineProto** ( PHP session arrays / serialized files )
* **Tdata** ( Telegram Desktop profile folder , extract relevant files )
* **LiveProto ( LP )** ( first-class citizen , SessionBridge is linked and can export / import LP files )

> If you need support for additional session types open an issue or contribute an adapter

| Type | From | To |
| --- | --- | --- |
| LiveProto String | :white_check_mark: | :white_check_mark: |
| LiveProto SQLite | :white_check_mark: | :white_check_mark: |
| Telethon String | :white_check_mark: | :white_check_mark: |
| Telethon SQLite | :white_check_mark: | :x: |
| Pyrogram String | :white_check_mark: | :white_check_mark: |
| Pyrogram SQLite | :white_check_mark: | :x: |
| Madeline String | :white_check_mark: | :x: |
| Tdata | :white_check_mark: | :x: |

---

## License

SessionBridge is released under the [`AGPLv3`](LICENSE)

---

## Contact

If you need help, open an issue or discuss changes via pull requests. For sensitive security issues, use the repository's security contact

* _Email_ : MRTakNone@gmail.com 
* _Telegram_ : https://TakNone.t.me

🎊 *Happy bridging !*