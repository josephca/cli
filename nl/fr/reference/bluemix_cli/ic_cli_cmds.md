---

copyright:

  years: 2018


lastupdated: "2018-06-21"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:tip: .tip}

# Commandes générales de l'interface CLI (ibmcloud)
{: #ibmcloud_cli}

Version : 0.7.1

L'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} fournit un ensemble de commandes qui sont regroupées par espace de nom pour que les utilisateurs puissent interagir avec {{site.data.keyword.Bluemix_notm}}.

A compter de la version 0.5.0, le client de ligne de commande {{site.data.keyword.Bluemix_notm}} inclut un client de ligne de commande Cloud Foundry dans son installation. Si vous avez installé votre propre interface CLI cf, n'utilisez pas à la fois les commandes CLI d'{{site.data.keyword.Bluemix_notm}}, `ibmcloud [commande]`, et les commandes CLI de Cloud Foundry, `cf [commande]`, de votre propre installation dans le même contexte. Utilisez à la place `ibmcloud cf [commande]` si vous désirez utiliser cf cli pour gérer les ressources Cloud Foundry dans le contexte CLI d'{{site.data.keyword.Bluemix_notm}}.  Notez que `ibmcloud cf api/login/logout/target` n'est pas admis et que vous devez utiliser `ibmcloud api/login/logout/target` à la place.

A compter de mai 2018, les commandes de l'interface CLI d'{{site.data.keyword.Bluemix_notm}} ont été changées de `bluemix` et `bx` en `ibmcloud`. Vous pouvez toutefois continuer à utiliser les commandes de l'interface CLI `bluemix` et `bx` jusqu'à ce qu'elles soient retirées.
{: tip}

Les listes ci-dessous répertorient les commandes prises en charge par l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}, en indiquant leurs noms, leurs arguments, leurs options, leurs prérequis, leurs descriptions, et des exemples.
{:shortdesc}

**Remarque :** la zone *Prérequis* répertorie les actions qui sont requises avant l'utilisation de la commande. Les commandes pour lesquelles aucune action n'est requise indiquent **Aucun**. Sinon, les prérequis peuvent inclure une ou plusieurs des actions suivantes :

<dl>
<dt>Noeud final</dt>
<dd>Un noeud final d'API doit être défini via <code>bluemix api</code> avant l'utilisation de la commande.</dd>
<dt>Connexion</dt>
<dd>La connexion avec la commande <code>bluemix login</code> est requise avant l'utilisation de cette commande.
Si vous vous connectez avec un ID fédéré, utilisez l'option '--sso' pour vous authentifier avec un code d'accès unique ou utilisez l'option '--apikey' pour vous authentifier avec une clé d'API. Dans la console {{site.data.keyword.Bluemix_notm}} sélectionnez **Gérer** &gt; **Sécurité** &gt; **Clés d'API de la plateforme** pour créer des clés d'API.
</dd>
<dt>Cible</dt>
<dd>La commande <code>bluemix target</code> doit être utilisée pour définir une organisation et un espace avant l'utilisation de cette commande.</dd>
<dt>Docker</dt>
<dd>L'interface de ligne de commande Docker (docker) doit être installée pour que vous puissiez exécuter cette commande.</dd>
</dl>


Utilisez les index du tableau suivant pour examiner les commandes ibmcloud fréquemment utilisées.

## Commandes générales ibmcloud
{: #ibmcloud_commands_index}

<table summary="Commandes générales ibmcloud.">
<caption>Tableau 1. Commandes générales ibmcloud</caption>
 <thead>
 <th colspan="5">Commandes générales ibmcloud</th>
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
Afficher l'aide générale pour les commandes intégrées de premier niveau et les espaces de nom pris en charge de l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}, ou l'aide d'une commande intégrée ou d'un espace de nom spécifique.

```
ibmcloud help [COMMAND|NAMESPACE]
```

<strong>Prérequis</strong> : Aucun

<strong>Options de commande</strong> :

   <dl>
   <dt>COMMAND|NAMESPACE (facultatif)</dt>
   <dd>Commande ou espace de nom pour lequel afficher l'aide. Si la commande ou l'espace de nom n'est pas spécifié, l'aide générale de l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} est affichée.</dd>
   </dl>



<strong>Exemples</strong> :

Afficher l'aide générale pour l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}} :

```
ibmcloud help
```

Afficher l'aide pour la commande `info` :

```
ibmcloud help info
```

## ibmcloud api
{: #ibmcloud_api}
Définir ou afficher le noeud final d'API {{site.data.keyword.Bluemix_notm}}.

```
ibmcloud api [API_ENDPOINT] [--unset] [--skip-ssl-validation]
```

<strong>Prérequis</strong> : Aucun

<strong>Options de commande</strong> :
   <dl>
   <dt>API_ENDPOINT (facultatif)</dt>
   <dd>Noeud final d'API ciblé. Par exemple, `https://api.chinabluemix.net`. Si l'option *API_ENDPOINT* et l'option `--unset` sont toutes les deux spécifiées, le noeud final d'API en cours est affiché.</dd>
   <dt>--unset (facultatif)</dt>
   <dd>Supprimer le paramètre de noeud final d'API.</dd>
   <dt>--skip-ssl-validation (facultatif)</dt>
   <dd>Ignorer la validation SSL des demandes HTTP.</dd>
   </dl>
<strong>Exemples</strong> :

Définir le noeud final d'API api.chinabluemix.net :

```
ibmcloud api api.chinabluemix.net
```

```
ibmcloud api https://api.chinabluemix.net --skip-ssl-validation
```

Afficher le noeud final d'API en cours :

```
ibmcloud api
```

Annuler la définition du noeud final d'API :

```
ibmcloud api --unset
```

## ibmcloud config
{: #ibmcloud_config}


Ecrire les valeurs par défaut dans le fichier de configuration.

```
ibmcloud config --http-timeout TIMEOUT_IN_SECONDS | --trace (true|false|path/to/file) | --color (true|false) | --locale (LOCALE|CLEAR) | --check-version (true|false)
```

<strong>Prérequis</strong> : Aucun

<strong>Options de commande</strong> :
   <dl>
   <dt>--http-timeout <i>TIMEOUT_IN_SECONDS</i></dt>
   <dd>Délai d'attente pour les demandes HTTP. La valeur par défaut est 60 secondes.</dd>
   <dt>--trace true|false|<i>path-to-file</i></dt>
   <dd>Consigne la trace des demandes HTTP sur le terminal ou dans le fichier spécifié.</dd>
   <dt>--color true|false</dt>
   <dd>Active ou désactive la sortie en couleurs. Elle est activée par défaut.</dd>
   <dt>--locale <i>LOCALE|CLEAR</i></dt>
   <dd>Définit un environnement local par défaut. Si LOCALE a pour valeur <i>CLEAR</i>, l'environnement local précédent est supprimé.</dd>
   <dt>--check-version true|false</dt>
   <dd>Active ou désactive la vérification de la version de l'interface de ligne de commande.</dd>
   </dl>

Une seule de ces options peut être indiquée à la fois.

<strong>Exemples</strong> :

Définir le délai d'attente des demandes HTTP à 30 secondes :

```
ibmcloud config --http-timeout 30
```

Activer la sortie de trace pour les demandes HTTP :

```
ibmcloud config --trace true
```

Consigner la trace des demandes HTTP dans le fichier spécifié */home/usera/my_trace* :

```
ibmcloud config --trace /home/usera/my_trace
```

Désactiver la sortie couleur :

```
ibmcloud config --color false
```

Définir l'environnement local zh_Hans :

```
ibmcloud config --locale zh_Hans
```

Effacer les paramètres d'environnement local :

```
ibmcloud config --locale CLEAR
```

## ibmcloud info
{: #ibmcloud_info}

Afficher les informations {{site.data.keyword.Bluemix_notm}} de base, notamment la région en cours, la version du contrôleur de cloud et certains noeuds finaux utiles tels que les noeuds finaux pour la connexion et l'échange de jeton d'accès.

```
ibmcloud info
```

<strong>Prérequis</strong> : Noeud final

## ibmcloud cf
{: #ibmcloud_cf}

Appeler l'interface CLI CF imbriquée

```
ibmcloud [-q, --quiet] cf COMMAND...
```

<strong>Prérequis</strong> : Aucun

<strong>Options de commande</strong> :
<dl>
  <dt>-q, --quiet</dt>
  <dd>Désactiver le message "Appel de commande cf..."</dd>
</dl>

<strong>Exemples</strong> :

Liste d'applications CF :

```
ibmcloud cf apps
```

Répertorier les services CF sans le message "Appel de commande cf...":

```
ibmcloud -q cf services
```

## ibmcloud login
{: #ibmcloud_login}

Connecter l'utilisateur.

```
ibmcloud login [-a API_ENDPOINT] [--sso] [-u USERNAME] [-p PASSWORD] [--apikey KEY | @KEY_FILE] [--no-iam] [-c ACCOUNT_ID] [-g RESOURCE_GROUP] [-o ORG] [-s SPACE]
```

<strong>Prérequis</strong> : Aucun

<!-- staging comment for Atlas 45: might need prereq for federated ID/SSO option unless we expect them to just view the details from the cf login command -->

<strong>Options de commande</strong> :
<dl>
  <dt> -a <i>API_ENDPOINT</i> (facultatif)</dt>
  <dd> Noeud final de l'API (par exemple : api.ng.bluemix.net)</dd>
  <dt> --apikey <i>API_KEY ou @API_KEY_FILE_PATH</i>
  <dd> Contenu de clé d'API ou chemin d'un fichier de clés d'API indiqué par @</dd>
  <dt> --sso (facultatif) </dt>
  <dd> Utiliser un code d'accès unique pour se connecter </dd>
  <dt> -u <i>USERNAME</i> (facultatif)</dt>
  <dd> Nom d'utilisateur</dd>
  <dt> -p <i>PASSWORD</i> (facultatif)</dt>
  <dd> Mot de passe</dd>
  <dt> -c <i>ACCOUNT_ID</i> (facultatif) </dt>
  <dd> ID du compte cible</dd>
  <dt> -g <i>RESOURCE_GROUP</i> (facultatif) </dt>
  <dd> Nom du groupe de ressources cible</dd>
  <dt> -o <i>ORG</i> (facultatif)</dt>
  <dd> Nom de l'organisation cible (obsolète, utilisez 'ibmcloud target -o ORGANISATION')</dd>
  <dt> -s <i>SPACE</i> (facultatif) </dt>
  <dd> Nom de l'espace cible (obsolète, utilisez 'ibmcloud target -s ESPACE')</dd>
  <dt> --no-iam </dt>
  <dd> Imposer une authentification avec un serveur de connexion plutôt qu'avec un système IAM public</dd>
  <dt> --skip-ssl-validation (facultatif) </dt>
  <dd> Ignorer la validation SSL des demandes HTTP. Cette option n'est pas recommandée.</dd>
</dl>

<strong>Exemples</strong> :

#### Connexion en mode interactif

```
ibmcloud login
```

Connectez-vous avec un nom d'utilisateur et un mot de passe, puis définissez un compte, une organisation et un espace cible :

```
ibmcloud login -u username -p password -c MyAccountID -o MyOrg -s MySpace
```

Connectez-vous avec un code d'accès unique et définissez un compte, une organisation et un espace cible

```
ibmcloud login --sso -c MyAccountID -o MyOrg -s MySpace
```

Connectez-vous avec une clé d'API et définissez des cibles :

#### Un compte est associé à une clé d'API

```
ibmcloud login --apikey api-key-string -o MyOrg -s MySpace
```

```
ibmcloud login --apikey @filename -o MyOrg -s MySpace
```

#### Aucun compte n'est associé à une clé d'API

```
ibmcloud login --apikey api-key-string -c MyAccountID -o MyOrg -s MySpace
```

```
ibmcloud login --apikey @fileName -c MyAccountID -o MyOrg -s MySpace
```

<strong>Remarque :</strong> si un compte est associé à la clé d'API, le passage à un autre compte n'est pas autorisé.

#### Utilisez un code d'accès unique

```
ibmcloud login -u UserID --sso
```

L'interface de ligne de commande fournira ensuite un lien d'URL et demandera un code d'accès :
```
One Time Code (Get one at https://URL_Link_To_Obtain_Passcode):
```

Ouvrez le lien dans un navigateur et laissez-vous guider pour obtenir le code secret. Entrez le code d'accès qui vous a été fourni dans la console. Vous devriez pouvoir vous connecter.

## ibmcloud logout
{: #ibmcloud_logout}

Déconnectez l'utilisateur.

```
ibmcloud logout
```

<strong>Prérequis</strong> : Aucun

## ibmcloud regions
{: #ibmcloud_regions}

Afficher les informations pour toutes les régions dans {{site.data.keyword.Bluemix_notm}}.

```
ibmcloud regions
```

<strong>Prérequis</strong> : Noeud final

## ibmcloud target
{: #ibmcloud_target}


Définir ou afficher le compte, la région, l'organisation ou l'espace cible :

```
ibmcloud target [-r REGION_NAME] [-c ACCOUNT_ID] [-g RESOURCE_GROUP] [--cf] [-o ORG] [-s SPACE]
```

<strong>Prérequis</strong> : Noeud final, Connexion

<strong>Options de commande</strong> :
   <dl>
   <dt>-r <i>REGION_NAME</i> (facultatif)</dt>
   <dd>Nom de la région vers laquelle commuter, par exemple 'us-south' ou 'eu-gb'.</dd>
   <dt>-c <i>ACCOUNT_ID</i> (facultatif)</dt>
   <dd>ID du compte à cibler.</dd>
   <dt>-g <i>RESOURCE_GROUP</i> (facultatif)</dt>
   <dd>Nom du groupe de ressources</dd>
   <dt>--cf</dt>
   <dd>Sélectionner l'organisation et l'espace cible de manière interactive</dd>
   <dt>-o <i>ORG_NAME</i> (facultatif)</dt>
   <dd>Nom de l'organisation à cibler.</dd>
   <dt>-s <i>SPACE_NAME</i> (facultatif)</dt>
   <dd>Nom de l'espace à cibler.</dd>
   </dl>
Si aucune de ces options n'est spécifiée, le compte, la région, l'organisation et l'espace en cours s'affichent.

<strong>Exemples</strong> :

Définir le compte, l'organisation et l'espace en cours :

```
ibmcloud target -c MyAccountID -o MyOrg -s MySpace
```

Basculer vers une nouvelle région :

```
ibmcloud target -r eu-gb
```

Afficher le compte, la région, l'organisation et l'espace en cours :

```
ibmcloud target
```

## ibmcloud update
{: #ibmcloud_update}

Mettre à jour l'interface de ligne de commande vers la version la plus récente.

```
ibmcloud update [-f]
```

<strong>Prérequis</strong> : Aucun

<strong>Options de commande</strong> :
<dl>
  <dt>-f</dt>
  <dd>Forcer la mise à jour sans confirmation. Privilège de superutilisateur (root) requis.</dd>
</dl>
