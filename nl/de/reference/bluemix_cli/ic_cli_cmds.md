---

copyright:

  years: 2018


lastupdated: "2018-06-21"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:tip: .tip}

# Allgemeine CLI-Befehle (ibmcloud)
{: #ibmcloud_cli}

Version: 0.7.1

Von der {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle (CLI) werden Befehle bereitgestellt, die nach Namensbereich für Benutzer zur Interaktion mit {{site.data.keyword.Bluemix_notm}} zusammengefasst sind.

Ab Version 0.5.0 enthält die Installation des {{site.data.keyword.Bluemix_notm}}-Befehlszeilenclients einen Cloud Foundry-Befehlszeilenclient. Wenn Sie eine eigene Cloud Foundry-Befehlszeilenschnittstelle installiert haben, dann verwenden Sie die Befehle der {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle (CLI) vom Typ `ibmcloud [command]` und die Befehle der Cloud Foundry-Befehlszeilenschnittstelle (CLI) vom Typ `cf [command]` Ihrer eigenen Installation nicht in demselben Kontext. Verwenden Sie stattdessen  `ibmcloud cf [command]`, wenn Sie Cloud Foundry-Ressourcen mit der Cloud Foundry-Befehlszeilenschnittstelle (CF-CLI) im Kontext der {{site.data.keyword.Bluemix_notm}}-CLI verwalten wollen.  Beachten Sie, dass `ibmcloud cf api/login/logout/target` nicht zulässig ist und Sie stattdessen `ibmcloud api/login/logout/target` verwenden müssen.

Ab Mai 2018 wird an Stelle der {{site.data.keyword.Bluemix_notm}}-CLI-Befehle `bluemix` und `bx` künftig der Befehl `ibmcloud` verwendet. Sie können die CLI-Befehle `bluemix` und `bx` jedoch auch weiterhin noch so lange verwenden, bis sie zu einem späteren Zeitpunkt entfernt werden.
{: tip}

In der nachfolgenden Liste finden Sie detaillierte Angaben zu den von der {{site.data.keyword.Bluemix_notm}}-CLI unterstützten Befehlen mit zugehörigen Namen, Argumenten, Optionen, Voraussetzungen, Beschreibungen und Beispielen.
{:shortdesc}

**Hinweis:** Unter *Voraussetzungen* wird aufgelistet, welche Aktionen vor der Verwendung des Befehls ausgeführt werden müssen. Für Befehle, für die keine Voraussetzungen erfüllt sein müssen, ist **Keine** angegeben. Andernfalls kann mindestens eine der folgenden Aktionen eine Voraussetzung sein:

<dl>
<dt>Endpunkt</dt>
<dd>Vor dem Verwenden des Befehls muss ein API-Endpunkt durch Absetzen des Befehls <code>bluemix api</code> definiert werden.</dd>
<dt>Anmeldung</dt>
<dd>Vor der Verwendung des Befehls ist die Anmeldung über den Befehl <code>bluemix login</code> erforderlich.
Verwenden Sie beim Anmelden mit einer eingebundenen ID die Option '--sso' für die Anmeldung mit einmaligem Kenncode oder verwenden Sie die Option '--apikey' für die Authentifizierung mit einem API-Schlüssel. Wechseln Sie in der {{site.data.keyword.Bluemix_notm}}-Konsole zum Erstellen von API-Schlüsseln zu **Verwalten** &gt; **Sicherheit** &gt; **Plattform-API-Schlüssel**.
</dd>
<dt>Ziel</dt>
<dd>Vor dem Verwenden des Befehls muss der Befehl <code>bluemix target</code> zum Definieren einer Organisation und eines Bereichs ausgeführt werden.</dd>
<dt>Docker</dt>
<dd>Die Docker-CLI (docker) muss installiert werden, um diesen Befehl auszuführen.</dd>
</dl>


Verwenden Sie die Indizes in der folgenden Tabelle als Referenz für die häufig verwendeten ibmcloud-Befehle. 

## Allgemeine ibmcloud-Befehle
{: #ibmcloud_commands_index}

<table summary="Allgemeine ibmcloud-Befehle">
<caption>Tabelle 1. Allgemeine ibmcloud-Befehle</caption>
 <thead>
 <th colspan="5">Allgemeine ibmcloud-Befehle</th>
 </thead>
 <tbody>
 <tr>
 <td>[ibmcloud help](ic_cli_cmds.html#ibmcloud_help)</td>
 <td>[ibmcloud api](ic_cli_cmds.html#ibmcloud_api)</td>
 <td>[ibmcloud config](ic_cli_cmds.html#ibmcloud_config)</td>
 <td>[ibmcloud info](ic_cli_cmds.html#ibmcloud_info)</td>
 <td>[ibmcloud cf](ic_cli_cmds.html#ibmcloud_cf)</td>
 </tr>
 <tr>
 <td>[ibmcloud login](ic_cli_cmds.html#ibmcloud_login) </td>
 <td>[ibmcloud logout](ic_cli_cmds.html#ibmcloud_logout) </td>
 <td>[ibmcloud regions](ic_cli_cmds.html#ibmcloud_regions)</td>
 <td>[ibmcloud target](ic_cli_cmds.html#ibmcloud_target)</td>
 <td>[ibmcloud update](ic_cli_cmds.html#ibmcloud_update)</td>
 </tr>
 </tbody>
 </table>
 
 ## ibmcloud help
{: #ibmcloud_help}
Zeigt die erweiterte Hilfe für integrierte Befehle und unterstützte Namensbereiche der obersten Ebene in der {{site.data.keyword.Bluemix_notm}}-CLI oder die Hilfe für einen bestimmten integrierten Befehl oder Namensbereich an.

```
ibmcloud help [COMMAND|NAMESPACE]
```

<strong>Voraussetzungen</strong>: Keine

<strong>Befehlsoptionen:</strong>

   <dl>
   <dt>COMMAND|NAMESPACE (optional)</dt>
   <dd>Der Befehl oder Namensbereich, für den die Hilfe angezeigt wird. Wenn nichts angegeben ist, wird die erweiterte Hilfe für die {{site.data.keyword.Bluemix_notm}}-CLI angezeigt.</dd>
   </dl>



<strong>Beispiele</strong>:

Erweiterte Hilfe für die {{site.data.keyword.Bluemix_notm}}-CLI anzeigen:

```
ibmcloud help
```

Hilfe für den Befehl `info` anzeigen:

```
ibmcloud help info
```

## ibmcloud api
{: #ibmcloud_api}
{{site.data.keyword.Bluemix_notm}}-API-Endpunkt festlegen oder anzeigen.

```
ibmcloud api [API_ENDPOINT] [--unset] [--skip-ssl-validation]
```

<strong>Voraussetzungen</strong>: Keine

<strong>Befehlsoptionen:</strong>
   <dl>
   <dt>API_ENDPOINT (optional)</dt>
   <dd>Der API-Endpunkt, der als Ziel verwendet wird, zum Beispiel `https://api.chinabluemix.net`. Wenn weder die Option *API_ENDPOINT* noch die Option `--unset` angegeben wird, wird der aktuelle API-Endpunkt angezeigt.</dd>
   <dt>--unset (optional)</dt>
   <dd>Entfernt die Einstellung für den API-Endpunkt.</dd>
   <dt>--skip-ssl-validation (optional)</dt>
   <dd>Umgeht die SSL-Validierung von HTTP-Anforderungen.</dd>
   </dl>
<strong>Beispiele</strong>:

Für den API-Endpunkt api.chinabluemix.net festlegen:

```
ibmcloud api api.chinabluemix.net
```

```
ibmcloud api https://api.chinabluemix.net --skip-ssl-validation
```

Aktuellen API-Endpunkt anzeigen:

```
ibmcloud api
```

Definition für den API-Endpunkt rückgängig machen:

```
ibmcloud api --unset
```

## ibmcloud config
{: #ibmcloud_config}


Standardwerte in die Konfigurationsdatei schreiben.

```
ibmcloud config --http-timeout TIMEOUT_IN_SECONDS | --trace (true|false|path/to/file) | --color (true|false) | --locale (LOCALE|CLEAR) | --check-version (true|false)
```

<strong>Voraussetzungen</strong>: Keine

<strong>Befehlsoptionen:</strong>
   <dl>
   <dt>--http-timeout <i>TIMEOUT_IN_SECONDS</i></dt>
   <dd>Der Zeitlimitwert für HTTP-Anforderungen. Der Standardwert ist 60 Sekunden.</dd>
   <dt>--trace true|false|<i>Dateipfad</i></dt>
   <dd>Trace für HTTP-Anforderungen mit Ausgabe auf Terminal oder in angegebener Datei aktivieren.</dd>
   <dt>--color true|false</dt>
   <dd>Farbausgabe aktivieren oder inaktivieren. Die Farbausgabe ist standardmäßig aktiviert.</dd>
   <dt>--locale <i>LOCALE|CLEAR</i></dt>
   <dd>Eine Standardländereinstellung festlegen. Wenn LOCALE den Wert <i>CLEAR</i> hat, wird die vorherige Ländereinstellung gelöscht.</dd>
   <dt>--check-version true|false</dt>
   <dd>CLI-Versionsprüfung aktivieren oder inaktivieren.</dd>
   </dl>

Es kann jeweils nur eine dieser Optionen gleichzeitig angegeben werden.

<strong>Beispiele</strong>:

HTTP-Anforderungszeitlimit auf 30 Sekunden setzen:

```
ibmcloud config --http-timeout 30
```

Traceausgabe für HTTP-Anforderungen aktivieren:

```
ibmcloud config --trace true
```

Traceausgabe für HTTP-Anforderungen in eine angegebene Datei */home/usera/my_trace* schreiben:

```
ibmcloud config --trace /home/usera/my_trace
```

Farbausgabe inaktivieren:

```
ibmcloud config --color false
```

Ländereinstellung auf 'zh_Hans' setzen:

```
ibmcloud config --locale zh_Hans
```

Ländereinstellungen löschen:

```
ibmcloud config --locale CLEAR
```

## ibmcloud info
{: #ibmcloud_info}

{{site.data.keyword.Bluemix_notm}}-Basisinformationen einschließlich aktueller Region, Cloud-Controller-Version und einigen nützlichen Endpunkten (zum Beispiel zum Anmelden und Austauschen von Zugriffstoken) anzeigen.

```
ibmcloud info
```

<strong>Voraussetzungen</strong>: Endpunkt

## ibmcloud cf
{: #ibmcloud_cf}

Eingebettete CF-CLI aufrufen

```
ibmcloud [-q, --quiet] cf COMMAND...
```

<strong>Voraussetzungen</strong>: Keine

<strong>Befehlsoptionen:</strong>
<dl>
  <dt>-q, --quiet</dt>
  <dd>Nachricht "Befehl cf wird aufgerufen..." inaktivieren</dd>
</dl>

<strong>Beispiele</strong>:

CF-Apps auflisten

```
ibmcloud cf apps
```

CF-Services ohne Nachricht "Befehl cf wird aufgerufen..." auflisten:

```
ibmcloud -q cf services
```

## ibmcloud login
{: #ibmcloud_login}

Benutzer anmelden.

```
ibmcloud login [-a API_ENDPOINT] [--sso] [-u USERNAME] [-p PASSWORD] [--apikey KEY | @KEY_FILE] [--no-iam] [-c ACCOUNT_ID] [-g RESOURCE_GROUP] [-o ORG] [-s SPACE]
```

<strong>Voraussetzungen</strong>: Keine

<!-- staging comment for Atlas 45: might need prereq for federated ID/SSO option unless we expect them to just view the details from the cf login command -->

<strong>Befehlsoptionen:</strong>
<dl>
  <dt> -a <i>API_ENDPOINT</i> (optional)</dt>
  <dd> API-Endpunkt (z. B.: api.ng.bluemix.net)</dd>
  <dt> --apikey <i>API_KEY oder @API_KEY_FILE_PATH</i>
  <dd> API-Schlüsselinhalt oder der Pfad einer API-Schlüsseldatei, die durch @ angegeben wird.</dd>
  <dt> --sso (optional) </dt>
  <dd> Einmaligen Kenncode zum Anmelden verwenden. </dd>
  <dt> -u <i>USERNAME</i> (optional)</dt>
  <dd> Der Benutzername.</dd>
  <dt> -p <i>PASSWORD</i> (optional)</dt>
  <dd> Das Kennwort.</dd>
  <dt> -c <i>ACCOUNT_ID</i> (optional) </dt>
  <dd> Die ID des Zielkontos.</dd>
  <dt> -g <i>RESOURCE_GROUP</i> (optional) </dt>
  <dd> Der Name der Zielressourcengruppe</dd>
  <dt> -o <i>ORG</i> (optional)</dt>
  <dd> Der Name der Zielorganisation (veraltet, 'ibmcloud target -o ORG' verwenden)</dd>
  <dt> -s <i>SPACE</i> (optional) </dt>
  <dd> Der Name des Zielbereichs (veraltet, 'ibmcloud target -s SPACE' verwenden)</dd>
  <dt> --no-iam </dt>
  <dd> Authentifizierung beim Anmeldeserver anstatt beim öffentlichen IAM erzwingen</dd>
  <dt> --skip-ssl-validation (optional) </dt>
  <dd> Umgeht die SSL-Validierung von HTTP-Anforderungen. Diese Option wird nicht empfohlen.</dd>
</dl>

<strong>Beispiele</strong>:

#### Interaktive Anmeldung

```
ibmcloud login
```

Anmeldung mit einem Benutzernamen und einem Kennwort und Festlegen des Kontos, der Organisation und des Bereichs:

```
ibmcloud login -u username -p password -c MyAccountID -o MyOrg -s MySpace
```

Anmeldung mit einmaligem Kenncode und Festlegen eines Zielkontos, einer Organisation und eines Bereichs:

```
ibmcloud login --sso -c MyAccountID -o MyOrg -s MySpace
```

Anmeldung mit API-Schlüssel und Festlegen von Zielen:

#### API-Schlüssel hat zugeordnetes Konto.

```
ibmcloud login --apikey api-key-string -o MyOrg -s MySpace
```

```
ibmcloud login --apikey @filename -o MyOrg -s MySpace
```

#### API-Schlüssel hat kein zugeordnetes Konto.

```
ibmcloud login --apikey api-key-string -c MyAccountID -o MyOrg -s MySpace
```

```
ibmcloud login --apikey @fileName -c MyAccountID -o MyOrg -s MySpace
```

<strong>Hinweis:</strong> Wenn der API-Schlüssel ein zugeordnetes Konto hat, ist ein Wechsel zu einem anderen Konto nicht zulässig.

#### Einmaligen Kenncode verwenden

```
ibmcloud login -u UserID --sso
```

Anschließend stellt die Befehlszeilenschnittstelle einen URL-Link bereit und fordert zur Eingabe eines Kenncodes auf:
```
One Time Code (Get one at https://URL_Link_To_Obtain_Passcode):
```

Öffnen Sie im Browser den Link, der Sie zu dem Kenncode führt. Wenn Sie an der Konsole den angegebenen Kenncode eingeben, sollten Sie in der Lage sein, sich anmelden.

## ibmcloud logout
{: #ibmcloud_logout}

Benutzer abmelden.

```
ibmcloud logout
```

<strong>Voraussetzungen</strong>: Keine

## ibmcloud regions
{: #ibmcloud_regions}

Zeigt die Informationen für alle Regionen in {{site.data.keyword.Bluemix_notm}} an.

```
ibmcloud regions
```

<strong>Voraussetzungen</strong>: Endpunkt

## ibmcloud target
{: #ibmcloud_target}


Zielkonto, Region, Organisation oder Bereich festlegen oder anzeigen.

```
ibmcloud target [-r REGION_NAME] [-c ACCOUNT_ID] [-g RESOURCE_GROUP] [--cf] [-o ORG] [-s SPACE]
```

<strong>Voraussetzungen</strong>: Endpunkt, Anmeldung

<strong>Befehlsoptionen:</strong>
   <dl>
   <dt>-r <i>REGION_NAME</i> (optional)</dt>
   <dd>Der Name der Region, in die gewechselt werden soll, z. B. 'us-south' oder 'eu-gb'.</dd>
   <dt>-c <i>ACCOUNT_ID</i> (optional)</dt>
   <dd>Die ID des Zielkontos.</dd>
   <dt>-g <i>RESOURCE_GROUP</i> (optional)</dt>
   <dd>Der Name der Ressourcengruppe.</dd>
   <dt>--cf</dt>
   <dd>Interaktive Auswahl der Zielorganisation und des Zielbereichs</dd>
   <dt>-o <i>ORG_NAME</i> (optional)</dt>
   <dd>Der Name der Zielorganisation.</dd>
   <dt>-s <i>SPACE_NAME</i> (optional)</dt>
   <dd>Der Name des Zielbereichs.</dd>
   </dl>
Wenn keine der Optionen angegeben wird, werden das aktuelle Konto, die aktuelle Region, die aktuelle Organisation und der aktuelle Bereich angezeigt.

<strong>Beispiele</strong>:

Aktuelles Konto, aktuelle Organisation und aktuellen Bereich festlegen:

```
ibmcloud target -c MyAccountID -o MyOrg -s MySpace
```

Zu einer neuen Region wechseln:

```
ibmcloud target -r eu-gb
```

Aktuelles Konto, aktuelle Region, aktuelle Organisation und aktuellen Bereich anzeigen:

```
ibmcloud target
```

## ibmcloud update
{: #ibmcloud_update}

Die Befehlszeilenschnittstelle auf die neueste Version aktualisieren.

```
ibmcloud update [-f]
```

<strong>Voraussetzungen</strong>: Keine

<strong>Befehlsoptionen:</strong>
<dl>
  <dt>-f</dt>
  <dd>Aktualisierung ohne Bestätigung erzwingen. Rootberechtigung ist erforderlich.</dd>
</dl>
