# Phonetic

Convert english to ipa

# Installation

Open your terminal and run:

```shell
composer require actcmsvn/phonetic
```

# Usage

Example

```php
<?php

use Phonetic\Language;
use Phonetic\Phonetics;

require __DIR__ . '/vendor/autoload.php';

$word = "Firewall is good Huy";

// txt
echo "<strong>Đây là format Text: </strong><br/>";
$phoneticSymbols = Phonetics::symbols($word, Phonetics::FORMAT_TXT, Language::EN_US);
echo $phoneticSymbols;

echo "<br/> <strong>Đây là format Array: </strong><br/>";
// array
$phoneticArray = Phonetics::symbols($word, 'array');
print_r($phoneticArray);

echo "<br/> <strong>Đây là format Json: </strong><br/>";
// json
$phoneticJson = json_encode(Phonetics::symbols($word, 'json'));
echo $phoneticJson;

//---------------------------------- use Array --------------------------------
echo "<br/> <strong>Xử lý array: </strong><br/>";
$phoneticSymbols = Phonetics::symbols($word, 'array');
$pronunciation = '';

foreach ($phoneticSymbols as $wordPhonetics) {
    // phần tử đầu tiên của mảng
    $firstPhoneticSymbol = reset($wordPhonetics);
    $pronunciation = $firstPhoneticSymbol;
    break;
}
echo $pronunciation;

/*
output:
Đây là format Text:
/ˈfaɪɹwɑɫ/ /ˈɪz/, /ɪz/ /ˈɡʊd/, /ɡɪd/ huy
Đây là format Array:
Array ( [firewall] => Array ( [0] => /ˈfaɪɹwɑɫ/ ) [is] => Array ( [0] => /ˈɪz/ [1] => /ɪz/ ) [good] => Array ( [0] => /ˈɡʊd/ [1] => /ɡɪd/ ) [huy] => Array ( [0] => huy ) )
Đây là format Json:
"{\"firewall\":[\"\\\/\\u02c8fa\\u026a\\u0279w\\u0251\\u026b\\\/\"],\"is\":[\"\\\/\\u02c8\\u026az\\\/\",\" \\\/\\u026az\\\/\"],\"good\":[\"\\\/\\u02c8\\u0261\\u028ad\\\/\",\" \\\/\\u0261\\u026ad\\\/\"],\"huy\":[\"huy\"]}"
Xử lý array:
/ˈfaɪɹwɑɫ/
*/
```

## NYSIIS encoding

```php
echo "<br/> <strong>Nysiis: </strong><br/>";
Phonetics::nysiis($word, 'txt');
echo '<br/>-------------------<br/>';
Phonetics::nysiis($word, 'txt');
echo '<br/>-------------------<br/>';
Phonetics::nysiis($word, 'txt');
/*
output:
[ firewall ] => FARAALL
[ is ] => A
[ good ] => GAAD
[ huy ] => HY

-------------------
[ firewall ] => FARAALL
[ is ] => A
[ good ] => GAAD
[ huy ] => HY

-------------------
[ firewall ] => FARAALL
[ is ] => A
[ good ] => GAAD
[ huy ] => HY
*/
```

## Soundex

```php
echo "<br/> <strong>Soundex: </strong><br/>";
Phonetics::soundex($word, 'txt');
/*
[ firewall ] => F640
[ is ] => I200
[ good ] => G300
[ huy ] => H000
 */
```
