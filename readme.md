# Список полезных сниппетов

## Битрикс

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
$APPLICATION->IncludeFile('/path/to/file.php', array('IBLOCK_ID' => 1), array('MODE' => 'php'));
```

#### Подключение шаблона после кеширования
```
if ($this->startResultCache()) 
{
	// do MySQL query
	// ...
	
	$this->endResultCache();
}
$this->includeComponentTemplate();
```

#### Кеширование в новом ядре
```
$cache = \Bitrix\Main\Data\Cache::createInstance();
if ($cache->initCache($TTL, $uniqueString, $initDir = false))
{
	$arProp = $cache->getVars();
}
elseif ($cache->startDataCache($TTL, $uniqueString, $initDir = false))
{
	// do MySQL query 
	// ...
	
	$cache->endDataCache($arProp);
}
```
