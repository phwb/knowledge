# Список полезных сниппетов

## Битрикс.

#### Пустая страница
```
define("NO_KEEP_STATISTIC", true);
define("NO_AGENT_CHECK", true);
require($_SERVER["DOCUMENT_ROOT"]."/bitrix/modules/main/include/prolog_before.php");

// TO DO here...

require($_SERVER["DOCUMENT_ROOT"]."/bitrix/modules/main/include/epilog_after.php");
```

#### Включаемая область
```
$arParams = array('IBLOCK_ID' => 1);
$arMode = array('MODE' => 'php');
$APPLICATION->IncludeFile('/path/to/file.php', $arParams, $arMode);
```

#### Кеширование в новом ядре
```
$cache = \Bitrix\Main\Data\Cache::createInstance();
if ($cache->initCache($TTL, $uniqueString, $initDir = false))
{
	$arProp = $cache->getVars();
}
else
{
	// ... do MySQL query ...
	$cache->startDataCache($TTL, $uniqueString, $initDir = false);
	$cache->endDataCache($arProp);
}
```
