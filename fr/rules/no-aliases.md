<!-- PHP Manual -->
# Pas d'alias

PHP a beaucoup de fonctions natives : la même fonction peut même avoir plusieurs noms, tels que `is_int` qui peut aussi être appelée `is_integer` ou `is_long`. En fait, `is_int` et `is_integer` sont aussi valables l'un que l'autre. Et `is_long` est conservé pour compatibilité ascendante, mais pourrait disparaître lors d'un ménage à venir dans les fonctions de PHP. 

Il est recommandé d'utiliser la fonction principale, et d'éviter les fonctions alias.

## Détails De La Règle

Cette règle cible les codes qui utilisent les fonctions alias, et signalent tout usage de ces derniers. La liste complète des alias est disponible sur dans la documentation de PHP. 

| Alias | Master |
|---|---|
| \_ | gettext |
| chop | rtrim |
| close | closedir |
| com\_get | com\_propget |
| com\_propset | com\_propput |
| com\_set | com\_propput |
| die | exit |
| diskfreespace | disk\_free\_space |
| doubleval | floatval |
| fbsql | fbsql\_db\_query |
| fputs | fwrite |
| gzputs | gzwrite |
| i18n\_convert | mb\_convert\_encoding |
| i18n\_discover\_encoding | mb\_detect\_encoding |
| i18n\_http\_input | mb\_http\_input |
| i18n\_http\_output | mb\_http\_output |
| i18n\_internal\_encoding | mb\_internal\_encoding |
| i18n\_ja\_jp\_hantozen | mb\_convert\_kana |
| i18n\_mime\_header\_decode | mb\_decode\_mimeheader |
| i18n\_mime\_header\_encode | mb\_encode\_mimeheader |
| imap\_create | imap\_createmailbox |
| imap\_fetchtext | imap\_body |
| imap\_getmailboxes | imap\_list\_full |
| imap\_getsubscribed | imap\_lsub\_full |
| imap\_header | imap\_headerinfo |
| imap\_listmailbox | imap\_list |
| imap\_listsubscribed | imap\_lsub |
| imap\_rename | imap\_renamemailbox |
| imap\_scan | imap\_listscan |
| imap\_scanmailbox | imap\_listscan |
| ini\_alter | ini\_set |
| is\_double | is\_float |
| is\_integer | is\_int |
| is\_long | is\_int |
| is\_real | is\_float |
| is\_writeable | is\_writable |
| join | implode |
| key\_exists | array\_key\_exists |
| ldap\_close | ldap\_unbind |
| magic\_quotes\_runtime | set\_magic\_quotes\_runtime |
| mbstrcut | mb\_strcut |
| mbstrlen | mb\_strlen |
| mbstrpos | mb\_strpos |
| mbstrrpos | mb\_strrpos |
| mbsubstr | mb\_substr |
| msql | msql\_db\_query |
| msql\_createdb | msql\_create\_db |
| msql\_dbname | msql\_result |
| msql\_dropdb | msql\_drop\_db |
| msql\_fieldflags | msql\_field\_flags |
| msql\_fieldlen | msql\_field\_len |
| msql\_fieldname | msql\_field\_name |
| msql\_fieldtable | msql\_field\_table |
| msql\_fieldtype | msql\_field\_type |
| msql\_freeresult | msql\_free\_result |
| msql\_listdbs | msql\_list\_dbs |
| msql\_listfields | msql\_list\_fields |
| msql\_listtables | msql\_list\_tables |
| msql\_numfields | msql\_num\_fields |
| msql\_numrows | msql\_num\_rows |
| msql\_regcase | sql\_regcase |
| msql\_selectdb | msql\_select\_db |
| msql\_tablename | msql\_result |
| mssql\_affected\_rows | sybase\_affected\_rows |
| mssql\_affected\_rows | sybase\_affected\_rows |
| mssql\_close | sybase\_close |
| mssql\_close | sybase\_close |
| mssql\_connect | sybase\_connect |
| mssql\_connect | sybase\_connect |
| mssql\_data\_seek | sybase\_data\_seek |
| mssql\_data\_seek | sybase\_data\_seek |
| mssql\_fetch\_array | sybase\_fetch\_array |
| mssql\_fetch\_array | sybase\_fetch\_array |
| mssql\_fetch\_field | sybase\_fetch\_field |
| mssql\_fetch\_field | sybase\_fetch\_field |
| mssql\_fetch\_object | sybase\_fetch\_object |
| mssql\_fetch\_object | sybase\_fetch\_object |
| mssql\_fetch\_row | sybase\_fetch\_row |
| mssql\_fetch\_row | sybase\_fetch\_row |
| mssql\_field\_seek | sybase\_field\_seek |
| mssql\_field\_seek | sybase\_field\_seek |
| mssql\_free\_result | sybase\_free\_result |
| mssql\_free\_result | sybase\_free\_result |
| mssql\_get\_last\_message | sybase\_get\_last\_message |
| mssql\_get\_last\_message | sybase\_get\_last\_message |
| mssql\_min\_client\_severity | sybase\_min\_client\_severity |
| mssql\_min\_error\_severity | sybase\_min\_error\_severity |
| mssql\_min\_message\_severity | sybase\_min\_message\_severity |
| mssql\_min\_server\_severity | sybase\_min\_server\_severity |
| mssql\_num\_fields | sybase\_num\_fields |
| mssql\_num\_fields | sybase\_num\_fields |
| mssql\_num\_rows | sybase\_num\_rows |
| mssql\_num\_rows | sybase\_num\_rows |
| mssql\_pconnect | sybase\_pconnect |
| mssql\_pconnect | sybase\_pconnect |
| mssql\_query | sybase\_query |
| mssql\_query | sybase\_query |
| mssql\_result | sybase\_result |
| mssql\_result | sybase\_result |
| mssql\_select\_db | sybase\_select\_db |
| mssql\_select\_db | sybase\_select\_db |
| mysql | mysql\_db\_query |
| mysql\_createdb | mysql\_create\_db |
| mysql\_db\_name | mysql\_result |
| mysql\_dbname | mysql\_result |
| mysql\_dropdb | mysql\_drop\_db |
| mysql\_fieldflags | mysql\_field\_flags |
| mysql\_fieldlen | mysql\_field\_len |
| mysql\_fieldname | mysql\_field\_name |
| mysql\_fieldtable | mysql\_field\_table |
| mysql\_fieldtype | mysql\_field\_type |
| mysql\_freeresult | mysql\_free\_result |
| mysql\_listdbs | mysql\_list\_dbs |
| mysql\_listfields | mysql\_list\_fields |
| mysql\_listtables | mysql\_list\_tables |
| mysql\_numfields | mysql\_num\_fields |
| mysql\_numrows | mysql\_num\_rows |
| mysql\_selectdb | mysql\_select\_db |
| mysql\_tablename | mysql\_result |
| ocibindbyname | oci\_bind\_by\_name |
| ocicancel | oci\_cancel |
| ocicolumnisnull | oci\_field\_is\_null |
| ocicolumnname | oci\_field\_name |
| ocicolumnprecision | oci\_field\_precision |
| ocicolumnscale | oci\_field\_scale |
| ocicolumnsize | oci\_field\_size |
| ocicolumntype | oci\_field\_type |
| ocicolumntyperaw | oci\_field\_type\_raw |
| ocicommit | oci\_commit |
| ocidefinebyname | oci\_define\_by\_name |
| ocierror | oci\_error |
| ociexecute | oci\_execute |
| ocifetch | oci\_fetch |
| ocifetchinto | oci\_fetch\_array, oci\_fetch\_row, oci\_fetch\_assoc, oci\_fetch\_object |
| ocifetchstatement | oci\_fetch\_all |
| ocifreecursor | oci\_free\_statement |
| ocifreedesc | oci\_free\_descriptor |
| ocifreestatement | oci\_free\_statement |
| ociinternaldebug | oci\_internal\_debug |
| ocilogon | oci\_connect |
| ocinewcollection | oci\_new\_collection |
| ocinewcursor | oci\_new\_cursor |
| ocinewdescriptor | oci\_new\_descriptor |
| ocinlogon | oci\_new\_connect |
| ocinumcols | oci\_num\_fields |
| ociparse | oci\_parse |
| ocipasswordchange | oci\_password\_change |
| ociplogon | oci\_pconnect |
| ociresult | oci\_result |
| ocirollback | oci\_rollback |
| ociserverversion | oci\_server\_version |
| ocisetprefetch | oci\_set\_prefetch |
| ocistatementtype | oci\_statement\_type |
| odbc\_do | odbc\_exec |
| odbc\_field\_precision | odbc\_field\_len |
| pdf\_add\_outline | pdf\_add\_bookmark |
| pg\_clientencoding | pg\_client\_encoding |
| pg\_setclientencoding | pg\_set\_client\_encoding |
| pos | current |
| recode | recode\_string |
| rewind | rewinddir |
| show\_source | highlight\_file |
| sizeof | count |
| snmpwalkoid | snmprealwalk |
| strchr | strstr |
| xptr\_new\_context | xpath\_new\_context |


Les exemples suivants sont considérés comme erronés : 

```php
<?php
if (is_long($valeur)) { 
	// FaireQuelquechose()
}

if (is_integer($value)) { 
	// FaireQuelquechose()
}
?>
```


Les exemples suivants sont corrects

```php
<?php

if (is_int($valeur)) { 
	// FaireQuelquechose()
}

?>
```

## Quand l'Éviter
* Si votre référence de codage a déjà fait le choix explicite et systématique d'utiliser un alias au lieu de la fonction maître, il n'y a pas d'intérêt à changer.

## Bibliographie

* [PHP functions aliases](http://php.net/manual/en/aliases.php)
