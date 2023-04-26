🌍
*[Català](README-ca.md) · [Čeština] (README-cs.md) ∙ [Deutsch](README-de.md) ∙ [Ελληνικά](README-el.md) ∙ [Anglès](README.md) ∙ [Español](README-es.md) ∙ [Français](README-fr.md) ∙ [Indonesia](README-id.md) ∙ [Italiano](README-it.md) ∙ [日本語](README-ja.md) ∙ [한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한국어](README-ko.md) ∙ [[한ki]](README-pl.md) ∙ [Português](README-pt.md) ∙ [Română](README-ro.md) ∙ [Русский](README-ru.md) ∙ [Slovenščina](README-sl.md) ∙ [Українська](README-uk.md) ∙ [简体中文](README-zh.md) ∙ [繁體中文](README-zh-Hant.md)*

# L'art de la línia de comandament

* Nota: Tinc previst revisar-ho i buscar un nou coautor que ajudi a ampliar-ho a una guia més completa. Tot i que és molt popular, podria ser més ampli i una mica més profund. Si us agrada escriure i esteu a prop de ser un expert en aquest material i esteu disposats a considerar ajudar, si us plau, envieu-me una nota a josh (0x40) holloway.com. -[jlevy](https://github.com/jlevy), [Holloway](https://www.holloway.com). Gràcies!*

- [Meta](#meta)
- [Conceptes bàsics](#basics)
- [Ús quotidià](ús #everyday)
- [Fitxers i dades de tractament](#processing-fitxers-i-dades)
- [Depuració del sistema](#system-depuració)
- [One-liners](#one-liners)
- [Obscur però útil](#obscure-però-útil)
- [només macOS](només #macos)
- [Només Windows](només #windows)
- [Més recursos](#more-recursos)
- [Avís legal](#disclaimer)

! [curl -s 'https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md' | egrep -o '`\w+`' | tr -d '`' | cowsay -W50] (cowsay.png)

La fluïdesa a la línia d'ordres és una habilitat sovint descuidada o considerada arcana, però millora la vostra flexibilitat i productivitat com a enginyer de maneres òbvies i subtils. Aquesta és una selecció de notes i consells sobre l'ús de la línia d'ordres que ens ha semblat útil quan treballem en Linux. Alguns consells són elementals i alguns són bastant específics, sofisticats o obscurs. Aquesta pàgina no és llarga, però si podeu utilitzar i recordar tots els elements aquí, en sabeu molt.

Aquest treball és el resultat de [molts autors i traductors] (AUTHORS.md).
Alguns d'això
[originalment] (http://www.quora.com/What-are-some-lesser-known-but-useful-Unix-commands)
[aparegut] (http://www.quora.com/What-are-the-most-useful-Swiss-army-knife-one-liners-on-Unix)
a [Quora](http://www.quora.com/What-are-some-time-saving-tips-that-every-Linux-user-should-know),
però des de llavors s'ha traslladat a GitHub, on persones amb més talent que l'autor original han fet nombroses millores.
[**Si us plau, envieu una pregunta**] (https://airtable.com/shrzMhx00YiIVAWJg) si teniu alguna pregunta relacionada amb la línia d'ordres. [**Si us plau, contribuïu**] (/CONTRIBUTING.md) si veieu un error o alguna cosa que podria ser millor!

## Meta

Abast:

- Aquesta guia és tant per a principiants com per a usuaris experimentats. Els objectius són *amplitud* (tot allò important), *especificitat* (posa exemples concrets del cas més comú) i *brevetat* ( coses evidents que no són essencials o digressions que podeu buscar fàcilment en un altre lloc ). Cada consell és essencial en alguna situació o estalvia significativament el temps sobre alternatives.
- Això està escrit per a Linux, a excepció de les seccions "[ macOS només ] ( #macos només )" i "[ Només Windows ] ( # windows-només ). Molts dels altres articles s'apliquen o es poden instal·lar en altres Unices o macOS ( o fins i tot Cygwin ).
- L’atenció es centra en Bash interactiu, tot i que molts consells s’apliquen a altres petxines i a les escriptures generals de Bash.
- Inclou tant les comandes Unix "estàndards" com les que requereixen instal·lacions especials de paquets, sempre que siguin prou importants per merèixer la inclusió.

Notes:

- Per mantenir-ho a una pàgina, el contingut s’inclou implícitament per referència. Ets prou intel·ligent per buscar més detalls en un altre lloc un cop coneguis la idea o l'ordre a Google. Utilitzeu "apt`, 'yum`,` dnf`, 'pacman', 'pip` o` brew` ( segons convingui ) per instal·lar nous programes.
- Utilitzeu [ Explainshell ] ( http://explainshell.com/) per obtenir un desglossament útil del que fan les comandes, opcions, canonades, etc.


## Bases

- Aprendre Bash bàsic. De fet, escriviu "home bash" i almenys desnatada tot el tema; és bastant fàcil seguir i no tant de temps. Les petxines alternatives poden ser agradables, però Bash és potent i sempre està disponible ( aprenentatge * només * zsh, peix, etc., mentre tempta el vostre propi portàtil, us restringeix en moltes situacions, com utilitzar servidors existents ).

- Obteniu més informació sobre almenys un editor basat en text. L’editor “nano` és un dels més senzills per a l’edició bàsica ( obertura, edició, estalvi, cerca ). Tanmateix, per a l’usuari d’energia d’un terminal de text, no hi ha cap substitut de Vim ( `vi` ), l’editor dur a aprendre, però venerable, ràpid i complet. Moltes persones també utilitzen els emacs clàssics, especialment per a tasques d’edició més grans. ( Per descomptat, és probable que qualsevol desenvolupador de programari modern que treballi en un projecte extens utilitzi només un editor basat en text pur i també hagi de familiaritzar-se amb els IDE i eines gràfiques modernes. )

- Documentació de cerca:
  - Sabeu llegir la documentació oficial amb "home" ( per a l'inquisitiu, "home" enumera els números de secció, p. 1 és comandes "regulars", 5 són fitxers / convencions, i 8 són per a l'administració ). Trobeu pàgines d’home amb `apropos`.
  - Sabeu que algunes comandes no són executables, sinó construccions de Bash i que podeu obtenir ajuda amb "ajuda" i "ajuda -d`. Podeu esbrinar si una comanda és executable, carcassa construïda o àlies mitjançant l'ús de "ordre tipus.
  - "curl engany.sh / command` donarà un breu "llàmina de xat" amb exemples comuns de com utilitzar una comanda de closca.

- Obteniu informació sobre la redirecció de sortida i entrada mitjançant `>` i `<` i canonades amb `|`. Coneixeu `>` sobreescriu el fitxer de sortida i `> >` s'afegeix. Obteniu informació sobre la stdout i el stderr.

- Obteniu informació sobre l'expansió del globus de fitxer amb "*" ( i potser?`i [` ...` ] ) i citant i la diferència entre el doble '' "" i el single. ( Vegeu més sobre l'expansió variable a continuació. )

- Conegui la gestió de llocs de treball de Bash: `&`, ** ctrl-z **, ** ctrl-c **, `jobs`, `fg`, `bg`, `kill`, etc.

- Coneixeu la `ssh` i els fonaments bàsics de l'autenticació sense contrasenya, mitjançant "ssh-agent", `ssh-add`, etc.

- Gestió bàsica de fitxers: "ls" i "ls -l` ( en particular, apreneu què cada columna de "ls -l` significa ), `less`, `head`, `tail` i `tail -f` ( o encara millor, `menys + F` ), `ln` i ` ln -s` ( aprendre les diferències i els avantatges dels enllaços durs versus suaus ), `cown`, `chmod`,` du` ( per a un resum ràpid de l'ús del disc: `du -hs *` ). Per a la gestió del sistema de fitxers, `df`, `mount`, `fdisk`, `mkfs`, `lsblk`. Obteniu més informació sobre quin inode és ( 'ls -i` o `df -i` ).

- Gestió bàsica de la xarxa: "ip` o "ifconfig`, 'dig`, 'traceroute`,` ruta.

- Aprendre i utilitzar un sistema de gestió de control de versions, com ara `git`.

- Conegueu bé les expressions regulars i les diverses banderes a `grep` /` per exemple. Val la pena conèixer les opcions `-i`, `-o`, `-A`, `-B` i `-C`.

- Aprendre a utilitzar "apt-get`, 'yum`, 'dnf` o 'pacman` ( depenent de distro ) per trobar i instal·lar paquets. I assegureu-vos que teniu "pip" per instal·lar eines de línia de comandament basades en Python ( algunes a continuació són més fàcils d'instal·lar mitjançant "pip` ).


## Ús de dia

- A Bash, utilitzeu ** Tab ** per completar arguments o enumerar totes les comandes disponibles i ** ctrl-r ** per cercar l’historial de comandaments ( després de prémer, escriviu a la cerca, premeu **ctrl-r ** repetidament per anar en bicicleta per més partits, premeu ** Enter ** per executar la comanda trobada, o toqueu la fletxa dreta per posar el resultat a la línia actual per permetre l'edició ).

- A Bash, utilitzeu ** ctrl-w ** per eliminar l'última paraula i ** ctrl-u ** per eliminar el contingut del cursor actual de nou a l'inici de la línia. Utilitzeu ** alt-b ** i ** alt-f ** per moure's per paraula, **ctrl-a ** per moure el cursor fins al començament de la línia, **ctrl-e** moure el cursor fins al final de la línia, **ctrl-k ** per matar fins al final de la línia, ** ctrl-l ** per netejar la pantalla. Vegeu "ledline de l'home" per a tots els claus predeterminats de Bash. Hi ha molt. Per exemple, ** alt-. ** cicles mitjançant arguments anteriors, i ** alt- *** amplia un guant.


- Alternativament, si us encanten les claus d'estil vi, utilitzeu "set -o vi` ( i "set -o emacs" per tornar-lo a posar ).

- Per editar comandes llargues, després d’establir el vostre editor ( per exemple `exportació EDITOR = vim` ), **ctrl-x ** **ctrl-e** obrirà el comandament actual en un editor per a l'edició de diverses línies. O en estil vi, ** escape-v**.

- Per veure comandes recents, utilitzeu la `història». Seguiu amb `!n` ( on `n` és el número de comanda ) per executar de nou. També hi ha moltes abreviatures que podeu utilitzar, el més útil probablement sigui `!$` per últim argument i `!!`per a l'última comanda ( vegeu "EXPANSIÓ HISTORYRIA" a la pàgina de l'home ). Tot i això, sovint es substitueixen fàcilment per **ctrl-r ** i ** alt-.**.

- Vés al directori de casa amb `cd`. Accés a fitxers relatius al directori domèstic amb el prefix `~` ( p. `~ / .bashrc` ). En els scripts de sh` es refereixen al directori domèstic com a `$ HOME`.

- Per tornar al directori de treball anterior: `cd -`.

- Si esteu a mig camí d’escriure una ordre, però canvieu d’opinió, toqueu ** alt-# ** per afegir un `#`al principi i introduïu-lo com a comentari ( o utilitzeu **ctrl-a **, ** #**, ** enter ** ). Podeu tornar-hi més endavant mitjançant la història del comandament.

- Utilitzeu `xargs` ( o `paral·lel` ). És molt potent. Tingueu en compte que podeu controlar quants articles s’executen per línia ( `-L` ) així com el paral·lelisme (` -P` ). Si no esteu segurs de si farà les coses bé, utilitzeu primer el ressò de les barres. A més, "-I { }" és útil. Exemples:
``
      trobar. -name '* .py' | xargs grep ere_function
      hosts de gats | xargs -I { } ssh root @ { } nom d'amfitrió
``

- "Pstree -p` és una pantalla útil de l'arbre de processos.

- Utilitzeu "pgrep" i "pkill" per trobar o indicar processos per nom (` -f` és útil ).

- Conegueu els diferents senyals que podeu enviar processos. Per exemple, per suspendre un procés, utilitzeu `kill -STOP [ pid ]`. Per a la llista completa, vegeu el senyal `man 7`

- Utilitzeu "nohofup" o "desposat" si voleu que un procés de fons continuï funcionant per sempre.

- Comproveu quins processos escolten a través de "nettstat -lntp` o 'ss -plat` ( per TCP; afegeix `-u` per UDP ) o `lsof -iTCP -sTCP: LISTEN -P -n` ( que també funciona en macOS ).

- Vegeu també "lsof" i "fuser" per a endolls i fitxers oberts.

- Vegeu "uptime" o "w` per saber quant temps s'ha executat el sistema.

- Utilitzeu "àlies" per crear dreceres per a comandes d'ús comú. Per exemple, "àlies ll =" ls -latr '' crea un nou àlies "ll`.

- Desa àlies, configuracions de closca i funcions que utilitzeu habitualment a `~ / .bashrc`, i [ arrange per a petxines d’inici de sessió per alimentar-lo ] ( Això farà que la vostra configuració estigui disponible en totes les vostres sessions de closca.

- Poseu la configuració de variables d’entorn, així com ordres que s’han d’executar quan inicieu la sessió a `~ / .bash_profile`. Es necessitarà una configuració separada per a petxines que es llancen a partir de logins gràfics d’entorn i “treballs de cron”.

- Sincronitzar els fitxers de configuració ( p. `.bashrc` i `.bash_profile` ) entre diversos ordinadors amb Git.

- Comprendre que es necessita cura quan les variables i els noms de fitxers inclouen espai blanc. Envolteu les vostres variables Bash amb pressupostos, p. "" $ OO "`. Preferiu les opcions "-0` o '-print0` per permetre als caràcters nuls delimitar noms de fitxers, p. `locar -0 patró | xargs -0 ls -al` o `find / -imprimir0 -tipus d | xargs -0 ls -al`. Per a iterar en noms de fitxers que contenen espai blanc en un bucle, configureu que el vostre IFS sigui una línia nova només mitjançant "IFS = $" \ n.

- En els scripts Bash, utilitzeu "set -x` ( o la variant 'set-v`, que registra l'entrada crua, incloses variables i comentaris no caducats ) per a la sortida de depuració. Utilitzeu modes estrictes tret que tingueu una bona raó per no: Utilitzeu "conjunt -e` per avortar errors ( codi de sortida no zero ). Utilitzeu "conjunt -u` per detectar usos variables no establerts. Penseu també en "conjunt -o pipefail" per avortar errors dins de les canonades ( tot i que llegiu-lo més si ho feu, ja que aquest tema és una mica subtil ). Per a scripts més implicats, també utilitzeu `trap` a EXIT o ERR. Un hàbit útil és iniciar un guió com aquest, cosa que el farà detectar i avortar per errors comuns i imprimir un missatge:
``
      pipefa de set -eu
      trampa "error" de l'echo: el guió ha fallat: vegeu la comanda fallida de dalt "ERR
``

- En els scripts Bash, els subshells ( escrits amb parèntesis ) són maneres convenients de agrupar ordres. Un exemple comú és traslladar-se temporalment a un directori de treball diferent, p.
``
      # fer alguna cosa en el dit corrent
      ( cd / alguns / altres / dir i altres comandaments )
      # continuar en dir original
``

- A Bash, tingueu en compte que hi ha molts tipus d’expansió variable. Existeix una comprovació d'una variable: `$ { nom:?missatge d'error }`. Per exemple, si un guió Bash requereix un sol argument, només cal escriure `input_file = $ { 1:?ús: $ 0 entrada_file }`. Si s'utilitza un valor per defecte si una variable està buida: `$ { nom: -predeterminat }`. Si voleu tenir un paràmetre addicional ( opcional ) afegit a l'exemple anterior, podeu utilitzar alguna cosa com "output_file = $ { 2: -logfile }`. Si s'omet $ 2` i, per tant, buida, "output_file" es fixarà en "logfile. Expansió aritmètica: `i = $ ( ( i ( 1 + 5% ) )`. Seqüències: `{ 1..10 }`. Reducció de cordes: `$ { var% suffix }` i $ { var # prefix }`. Per exemple, si `var = foo.pdf`, llavors `echo $ { var%.pdf } .txt` estampes `foo.txt`.

- Expansió de la cursa utilitzar "{" ... "}" pot reduir haver de tornar a escriure combinacions de text similars i automatitzar elements.  Això és útil en exemples com "mv foo. { txt, ppdf } algun dir` ( que mou els dos fitxers ), `cp erefile {,.bak } `( que s'estén a `cp erefile erefile.bak` ) o `mkdir -p test- { a, b, c } / subtest- { } que crea totes les combinacions possibles i un directori. L’expansió de la cursa es realitza abans de qualsevol altra expansió.

- L’ordre d’expansions és: expansió de braçalet; expansió de tilde, expansió de paràmetres i variables, expansió aritmètica i substitució de comandaments ( es va posar de manera esquerra a dreta ); divisió de paraules; i expansió del nom de fitxer. ( Per exemple, no es pot expressar amb variables que utilitzin `{ 1..20 }` <TOG1> { a .. $ b $`. Utilitzeu "seq" o un "clo per a" en lloc d'això, per exemple, "seq $ a $ b` o ` per ( ( i = a; i < = b; i + + ); do

- La sortida d'una comanda es pot tractar com un fitxer mitjançant `< ( alguna ordre )` ( coneguda com a substitució de processos ). Per exemple, compareu `/etc/hosts locals amb un remot:
`` sh
      dif / etc / hosts < ( ssh algun gat / etc / hosts )
``

- Quan escriviu scripts, potser voldreu posar tot el vostre codi en clapes arrissades. Si falta el braçalet de tancament, se li impedirà que el vostre guió s’executarà a causa d’un error de sintaxi. Això té sentit quan es descarregarà el vostre script des del web, ja que impedeix que els scripts parcialment descarregats s'executin:
``
{
      # El vostre codi aquí
}
``

- Un "document d'aquí" permet [ redirecció de múltiples línies d'entrada ] ( https://www.tldp.org/LDP/abs/html/here-docs.html) com si fos d'un fitxer:
``
gat < < EOF
entrada
en diverses línies
EOF
``

- A Bash, redirigiu tant la sortida estàndard com l'error estàndard mitjançant: "alguns comandaments > logfile 2 > & 1` o "alguns comandaments i > logfile`. Sovint, per assegurar-se que una comanda no deixa un mànec de fitxer obert a l’entrada estàndard, lligant-la al terminal on esteu, també és una bona pràctica afegir `< / dev/nul.

- Utilitzeu "home ascii" per a una bona taula ASCII, amb valors hex i decimals. Per obtenir informació general de codificació, "man unicode", "man utf-8` i "man llatina1" són útils.

- Utilitzeu la pantalla o [ 'tmux` ] ( https://tmux.github.io/) per multiplexar la pantalla, especialment útil en sessions remotes i per desmunta i tornar a enganxar a una sessió. "byobu` pot millorar la pantalla o el tmux proporcionant més informació i una gestió més fàcil. Una alternativa més mínima per a la persistència de sessió només és [ `dtach` ] ( https://github.com/bogner/dtach).

- En ssh, saber portar túnel amb `-L` o `-D` ( i de tant en tant `-R` ) és útil, p. per accedir a llocs web d’un servidor remot.

- Pot ser útil fer algunes optimitzacions a la configuració ssh; per exemple, aquest ~ / .ssh / config` conté configuracions per evitar connexions caigudes en determinats entorns de xarxa, utilitza compressió ( que és útil amb scp sobre connexions d'amplada baixa de banda ) i canals multiplex al mateix servidor amb un fitxer de control local:
``
      TCPKeepAlive = sí
      ServerAliveInterval = 15
      ServerAliveCountMax = 6
      Compressió = sí
      Automàtica ControlMaster
      ControlPath / tmp /% r @% h:% p
      ControlPersista sí
``

- Algunes altres opcions rellevants per a ssh són sensibles a la seguretat i haurien d’estar habilitades amb cura, p. per subnet o amfitrió o en xarxes de confiança: `StrictHostKeyCheking = no`, `ForwardAgent = sí`

- Considereu [`mosh` ] ( https://mosh.mit.edu/) una alternativa a ssh que utilitza UDP, evitant connexions caigudes i afegint comoditat a la carretera ( requereix la configuració del servidor ).

- Per obtenir els permisos en un fitxer en forma octal, que és útil per a la configuració del sistema, però no disponible a `ls` i fàcil de bungle, utilitzeu alguna cosa com
`` sh
      stat -c '% A% a% n '/ etc / timezone
``

- Per a la selecció interactiva de valors a partir de la sortida d’una altra comanda, utilitzeu [ `percol` ] ( o https://github.com/mooz/percol)` fzf` [ ] (

- Per a la interacció amb fitxers basats en la sortida d’una altra comanda ( com `git` ), utilitzeu `fpp` ( [ PathPicker ] ( https://github.com/facebook/PathPicker)).

- Per a un servidor web senzill per a tots els fitxers del directori actual ( i subdirs ), a disposició de qualsevol persona de la vostra xarxa, utilitzeu:
`python -m SimpleHTTPServer 7777` ( per al port 7777 i Python 2 ) i `python -m http.server 777` ( per al port 777 i Python 3 ).

- Per executar una comanda com a altre usuari, utilitzeu `sudo`. Els defectes per funcionar com a arrel; utilitzeu `-u` per especificar un altre usuari. Utilitzeu "-i` per iniciar la sessió com a usuari ( se us demanarà _la vostra_ contrasenya ).

- Per canviar la closca a un altre usuari, utilitzeu el nom d'usuari o el nom d'usuari. Aquest últim amb "-" obté un entorn com si un altre usuari només entrés. Omitting the username predeterminat a arrel. Se us demanarà la contrasenya _ de l'usuari a què esteu commuta.

- Coneixeu el límit [ 128K ] ( https://wiki.debian.org/CommonErrorMessages/ArgumentListTooLong) a les línies de comandament. Aquest error "llista d'argument massa llarg" és habitual quan la comodina coincideixi amb un gran nombre de fitxers. ( Quan això passi alternatives com "find" i "xargs" pot ajudar. )

- Per a una calculadora bàsica ( i, per descomptat, l’accés a Python en general ), utilitzeu l’intèrpret “python`. Per exemple,
``
> > > 2 + 3
5
``


## Fitxers i dades de processament

- Per localitzar un fitxer per nom al directori actual, `troba. -nom '* alguna cosa *' ( o similar ). Per trobar un fitxer en qualsevol lloc per nom, utilitzeu "localitzeu alguna cosa" ( però tingueu en compte que "updatedb" pot no haver indexat fitxers creats recentment ).

- Per a la cerca general a través de fitxers de fonts o dades, hi ha diverses opcions més avançades o més ràpides que "grep -r`, inclòs ( en ordre brut de més gran a més recent ) [ `ack` ] ( https://github.com/beyondgrep/ack2), `ag` [ ] ( https://github.com/ggreer/the_silver_searcher) "el seargent" ( <TAGTA> 1> <GTA.

- Per convertir HTML al text: `lynx -dump -stdin`

- Per a Markdown, HTML i tot tipus de conversió de documents, proveu [ ` pandoc` ] ( http://pandoc.org/). Per exemple, convertir un document de marcatge al format Word: `pandoc README.md - de la marca --to docx -o temp.docx`

- Si heu de manejar XML, `xmlstarlet` és vell però bo.

- Per a JSON, utilitzeu [ ` jq` ] ( http://stedolan.github.io/jq/). Per a ús interactiu, vegeu també [ ` jid` ] ( https://github.com/simeji/jid) i [ 'jiq` ] (

- Per a YAML, utilitzeu [ 'shyaml` ] ( https://github.com/0k/shyaml).

- Per a fitxers Excel o CSV, [ csvkit ] ( https://github.com/onyxfish/csvkit) proporciona `in2csv`, `csvcut`, `csvjoin`, `csvgrep`, etc.

- Per a Amazon S3, [ `s3cmd` ] ( https://github.com/s3tools/s3cmd) és convenient i [ `s4cmd` ] ( https://github.com/bloomreach/s4cmd) és més ràpid. Les [ `aws` ] ( https://github.com/aws/aws-cli) i les [ ` saws` ] ( https://github.com/donnemartin/saws) són essencials per a altres tasques relacionades amb l'AWS.

- Coneixeu les opcions "sort" i "uniq`, incloses les opcions de uniq '-u` i '-d` - vegeu una línia a continuació. Vegeu també `comm`.

- Saber sobre "tallar", "paste" i "unir-se" per manipular fitxers de text. Moltes persones utilitzen "tallar", però s'obliden de "join.

- Saber sobre "wc" comptar les línies noves (` -l` ), caràcters (` - m` ), paraules ( '-w` ) i bytes ( '-c` ).

- Sabeu sobre "tee" copiar de stdin a un fitxer i també a stdout, com a "ls -al | tee file.txt`.

- Per a càlculs més complexos, inclosos els camps d’agrupació, reversió i càlculs estadístics, considereu [ ` datamash` ] ( https://www.gnu.org/software/datamash/).

- Sabeu que la localitat afecta moltes eines de línia de comandament de maneres subtils, inclosa l’ordre d’ordenació ( col·lació ) i el rendiment. La majoria de les instal·lacions de Linux configuraran `LANG` o altres variables locals a un entorn local com l’anglès nord-americà. Però tingueu consciència que la classificació canviarà si canvieu de lloc. I sé que les rutines i18n poden fer funcionar una mena o altres comandes * moltes vegades * més lentes. En algunes situacions ( com ara les operacions establertes o les operacions d'uniquitat a continuació ) podeu ignorar amb seguretat les rutines i18n lentes i utilitzar una comanda tradicional basada en bytes, mitjançant "export LC_ALL = C`.

- Podeu configurar un entorn de comanda específic prefixant la seva invocació amb la configuració de la variable d’entorn, com a la data `TZ = Pacific / Fiji`.

- Coneixeu el "awk" bàsic i "sed" per a la fusió de dades senzilles. Vegeu [ Un sol enllaç ] ( # un-liners ) per a exemples.

- Per substituir totes les ocurrències d’una cadena al seu lloc, en un o més fitxers:
`` sh
      perl -pi.bak -e 's /old-string / new string / g' my-files- * .txt
``

- Per canviar el nom de diversos fitxers i / o cercar i substituir dins dels fitxers, proveu [`emprenance` ] ( https://github.com/jlevy/repren). En alguns casos, l'ordre "renam` també permet múltiples noms, però tingueu cura que la seva funcionalitat no sigui la mateixa en totes les distribucions de Linux. )
`` sh
      # Nom complet de noms de fitxers, directoris i contingut foo - > barra:
      repren -full --preserve-cas - de foo - a bar .
      # Recuperar fitxers de còpia de seguretat qualsevol cosa.bak - > qualsevol cosa:
      repren -renames - de '(.*) \ .bak '- a '\ 1' * .bak
      # Igual que anteriorment, utilitzant el nom de nom, si està disponible:
      nom de nom "s /\ .bak $ //" * .bak
``

- Com diu la pàgina de l’home, “rsync` realment és una eina de còpia de fitxers ràpida i extraordinàriament versàtil. És conegut per sincronitzar entre màquines, però és igualment útil localment. Quan les restriccions de seguretat permeten, utilitzar "rsync" en lloc de "scp" permet recuperar una transferència sense reiniciar-se des de zero. També es troba entre les [ maneres més ràpides ] ( https://web.archive.org/web/20130929001850/http://linuxnote.net/jianingy/en/linux/a-fast-way-to-remove-huge-number-of-files.html) per eliminar un gran nombre de fitxers:
`` sh
mkdir buit && rsync -r -superat buit / algun dir i & rmdir algun dir
``

- Per controlar el progrés quan processen fitxers, utilitzeu [` pv` ] ( http://www.ivarch.com/programs/pv.shtml), [` pycp` ] ( https://github.com/dmerejkowsky/pycp), [`pmonitor` ] ( <TAGress> 1, `d status = progress`.

- Utilitzeu "shuf" per remenar o seleccionar línies aleatòries d'un fitxer.

- Conegueu les opcions de "sort. Per a números, utilitzeu `-n` o `-h` per gestionar números llegibles per humans ( p. de `du -h` ). Sabeu com funcionen les claus ( '-t` i '-k` ). En particular, mireu que heu d'escriure "-k1,1` per ordenar només el primer camp; '-k1` 
