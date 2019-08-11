# PYCOLEE COMMIT GUIDELINE - COME SCRIVERE UN MESSAGGIO DI COMMIT IN GIT

## **Italian translation only. English translation will be available soon!!!**

## **Indice**
1. [Prefazione](#prefazione)
2. [Le 7 regole per scrivere un buon messaggio di commit](#le-7-regole-per-scrivere-un-buon-messaggio-di-commit)
	1. [Separare l'oggetto dal corpo del testo usando una riga vuota](#separare-l-oggetto-dal-corpo-del-testo-usando-una-riga-vuota)
	2. [Non usare più di 50 caratteri per l'oggetto della commit](#non-usare-piu-di-50-caratteri-per-l-oggetto-della-commit)
	3. [Capitalizzare l'oggetto della commit](#capitalizzare-l-oggetto-della-commit)
	4. [Non mettere il punto alla fine dell'oggetto della commit](#non-mettere-il-punto-alla-fine-dell-oggetto-della-commit)
	5. [Scrivere l'oggetto della commit usando l'imperativo](#scrivere-l-oggetto-della-commit-usando-l-imperativo)
	6. [Il corpo della commit deve andare a capo ogni 72 caratteri](#il-corpo-della-commit-deve-andare-a-capo-ogni-72-caratteri)
	7. [Usare il corpo della commit per spiegare cosa e perché invece di come](#usare-il-corpo-della-commit-per-spiegare-cosa-e-perche-invece-di-come)
3. [Git commit message emoji](#git-commit-message-emoji)
4. [Conclusione](#conclusione)

Questa guida vuole essere un supporto su come devono essere scritti i messaggi di commit per il progetto Pycolee.

### Prefazione

**L'importanza di scrivere bene i messaggi di commit**

Se osserviamo i messaggi di commit degli sviluppatori all'interno di un progetto di lavoro (piattaforme quali Github o Gitlab, repository interni IAD) troveremo facilmente messaggi di commit più o meno lunghi. Vediamone un esempio facendoci stampare in output sul nostro terminale gli ultimi 5 messaggi di commit precedenti al 26 Marzo 2009:

> **$ git log --oneline -5 --author cbeams --before "Fri Mar 26 2009"**
>
> **e5f4b49 Re-adding ConfigurationPostProcessorTests after its brief removal in r814. @Ignore-ing the testCglibClassesAreLoadedJustInTimeForEnhancement() method as it turns out this was one of the culprits in the recent build breakage. The classloader hacking causes subtle downstream effects, breaking unrelated tests. The test method is still useful, but should only be run on a manual basis to ensure CGLIB is not prematurely classloaded, and should not be run as part of the automated build.**
>
> **2db0f12 fixed two build-breaking issues: + reverted ClassMetadataReadingVisitor to revision 794 + eliminated ConfigurationPostProcessorTests until further investigation determines why it causes downstream tests to fail (such as the seemingly unrelated ClassPathXmlApplicationContextTests)**
>
> **147709f Tweaks to package-info.java files**
>
> **22b25e0 Consolidated Util and MutableAnnotationUtils classes into existing AsmUtils**
>
> **7f96f57 polishing**

Se osserviamo attentamente l'esempio vedremo messaggi di commit molto lunghi ed altri molto brevi, che iniziano con la prima lettera maiuscola o con la prima lettera minuscola, che finiscono o non finiscono con un punto. Lo scopo di questa guida è quello di istruire lo sviluppatore dimostrandogli l'importanza dello scrivere bene i messaggi di commit.

Iniziamo con il prendere esempio da chi i messaggi di commit li scrive formalmente bene. Se siete curiosi vi consiglio di dare un'occhiata ad uno dei tanti repository di [Tim Pope](https://github.com/tpope/vim-pathogen/commits/master) o il repository del [Kernel di Linux](https://github.com/torvalds/linux/commits/master). Chi contribuisce allo sviluppo di questi repository sa bene quanto sia importante scrivere un messaggio di commit formalmente corretto in quanto è e sarà di aiuto per il futuro non solo a loro stessi ma anche agli altri.

Se all'interno di un progetto ci si trova con l'avere messaggi di commit confusionari è perché lo sviluppatore non si è mai curato di andare a leggere la documentazione di Git o di fare un semplice help del comando `git log`. Un log ben curato è una cosa bella e utile. Comandi quali `git blame`, `revert`, `rebase`, `log`, `shortlog` acquistano nuova vita. Il successo a lungo termine di un progetto si basa tra l'altro sulla sua manutenibilità e un manutentore ha pochi strumenti più potenti del log per il suo progetto. Vale la pena dedicare del tempo per imparare a prendersi cura di ciò. All'inizio, ciò che può essere una seccatura diventerà presto un'abitudine e alla fine una fonte di orgoglio e produttività per tutti i soggetti coinvolti.

La maggior parte dei linguaggi di programmazione ha convenzioni consolidate su ciò che costituisce uno stile idiomatico (naming convention), formattazione e così via. Ci sono variazioni su queste convenzioni, naturalmente, ma la maggior parte degli sviluppatori concorda sul fatto che sceglierne una e attenersi ad essa è molto meglio del caos che ne consegue quando ognuno fa a modo suo. L'approccio di un team al suo log di commit non dovrebbe essere diverso. Per creare una cronologia delle revisioni utile, i team devono innanzitutto concordare una convenzione di messaggio di commit che definisca almeno le seguenti tre cose:
* Stile (Sintassi di markup, margini di testo, grammatica, capitalizzazione, punteggiatura);
* Contenuto;
* Metadata.

Andiamo a definire quindi le 7 regole per scrivere un buon messaggio di commit.

### Le 7 regole per scrivere un buon messaggio di commit

Ricordatevi di tenere a mente [tutto](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html) [quello](https://www.git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project#_commit_guidelines) [che](https://github.com/torvalds/subsurface-for-dirk/blob/master/README#L92-L120) [vi](http://who-t.blogspot.com/2009/12/on-commit-messages.html) [abbiamo](https://github.com/erlang/otp/wiki/writing-good-commit-messages) [detto prima](https://github.com/spring-projects/spring-framework/blob/30bce7/CONTRIBUTING.md#format-commit-messages).


1. Separare l'oggetto dal corpo del testo usando una riga vuota;
2. Non usare più di 50 caratteri per l'oggetto della commit;
3. Capitalizzare l'oggetto della commit;
4. Non mettere il punto alla fine dell'oggetto della commit;
5. Scrivere l'oggetto della commit usando l'imperativo;
6. Il corpo della commit deve andare a capo ogni 72 caratteri;
7. Usare il corpo della commit per spiegare cosa e perché invece di come.

Esempio:

> Summarize changes in around 50 characters or less
> 
> More detailed explanatory text, if necessary. Wrap it to about 72
> characters or so. In some contexts, the first line is treated as the
> subject of the commit and the rest of the text as the body. The
> blank line separating the summary from the body is critical (unless
> you omit the body entirely); various tools like `log`, `shortlog`
> and `rebase` can get confused if you run the two together.
> 
> Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.
> 
> Further paragraphs come after blank lines.
>
>  - Bullet points are okay, too
>
>  - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here
>
> If you use an issue tracker, put references to them at the bottom,
like this:
> 
> Resolves: #123
>
> See also: #456, #789

### 1. Separare l'oggetto dal corpo del testo usando una riga vuota

Il manuale del comando `git commit` cita "**Anche se non richiesto è sempre meglio mettere il messaggio di commit su una sola riga (meno di 50 caratteri) che riepiloga la modifica, seguita da una riga vuota e quindi da una descrizione più approfondita. Il testo fino alla prima riga vuota in un messaggio di commit viene considerato come titolo di commit e tale titolo viene utilizzato in Git. Ad esempio, Git-format-patch (1) trasforma una commit in una email e utilizza il titolo sulla riga Oggetto e il resto del commit nel corpo.**"

Non tutte le commit richiedono oblligatoriamente oggetto e body, a volte il solo oggetto basta e avanza. Esempio:

> Fix errata corrige testo introduzione user guide 

Come si può notare in pochi caratteri abbiamo reso l'idea di ciò che è stato fatto. Se l'utente vuole sapere come è stato fatto potrà vedere con un comando quale `diff` o `git show` il tipo di cambiamento che è avvenuto. 

Se per esempio crediamo che sia necessario aggiungere qualche cosa di più al nostro messaggio di commit possiamo scrivere il corpo:

> Fix errata corrige testo introduzione user guide 
>
> L'introduzione era sbagliata e non consona a quello che era
> la prefazione di ciò che si voleva comunicare all'interno
> del documento.

Usando un comando quale `git log --oneline` avremo il seguente messaggio di log:

> 42e769 Fix errata corrige testo introduzione user guide

Noterete quinti quanto è importante scrivere un oggetto della commit che sia separato dal resto del corpo.

### 2. Non usare più di 50 caratteri per l'oggetto della commit;

Limitare l'oggetto della commit a solo 50 caratteri aiuta lo sviluppatore a mantenere i log chiari e leggibili e a spiegare in maniera chiara e concisa cosa si vuole dire.

> **ATTENZIONE: Se avete difficoltà nel riassumere in 50 caratteri quello che volete dire in quanto le modifiche che state rilasciando sono tante allora la buona norma sarà l'uso dei commit atomici.**

L'interfaccia utente di GitHub si appoggia fermamente su queste convenzioni, infatti avvisa se si superano i 50 caratteri e tronca il soggetto se supera i 72 caratteri mettendo 3 puntini consecutivi.

### 3. Capitalizzare l'oggetto della commit

Per dirla in maniera breve e consisa scrivere così:

* Fixare sommario documento

e non:

* fixare sommario documento

### 4. Non mettere il punto alla fine dell'oggetto della commit

All'interno dell'oggetto della commit non serve il punto. Esempio:

* Non usare punto alla fine dell'oggetto

### 5. Scrivere l'oggetto della commit usando l'imperativo

Usare l'imperativo significa semplicemente "**parlato o scritto come se si impartisse un comando**". Esempi:
* Chiudi la porta
* Pulisci la tua camera
* Porta fuori la spazzatura

Avete notato che le 7 regole per scrivere in modo corretto un messaggio di commit usano tutte l'imperativo? Usare l'imperativo può risultare rude e un tantino maleducato ma è perfetto per scrivere un oggetto di commit.

Notate ad esempio i messaggi di default dei comandi `git merge` e `git revert`, essi usano l'imperativo.

`git merge`:
> Merge branch 'myfeature'

`git revert`:
> Revert "Add the thing with the stuff"
>
> This reverts commit cc87791524aedd593cff5a74532befe7ab69ce9d.

Vediamo altri esempi di oggetti di commit imperativi:
* Rilasciare versione 1.0.0
* Rimuovere metodi deprecati
* Aggiornare documentazione iniziale

Se si hanno difficoltà sul come scrivere un oggetto di una commit nella maniera corretta eccovi un semplice trucchetto che potrà tornarvi utile:
* Se applicata questa modifica vorrà **rilasciare versione 1.0.0**
* Se applicata questa modifica vorrà **rimuovere metodi deprecati**
* Se applicata questa modifica vorrà **aggiornare documentazione iniziale**

**RICORDATE: l'imperativo va usato solo nell'oggetto della commit.**

### 6. Il corpo della commit deve andare a capo ogni 72 caratteri

Git non è in grado di eseguire il wrap del testo in automatico. Se non si usa questo piccolo accorgimento si finisce con l'avere nei messaggi di commit del testo mozzato in maniera errata. Usando solo 72 caratteri permettiamo a Git di avere un sacco di spazio in più quando indentare.

Ad oggi gli IDE di sviluppo non sono in grado di effettuare il wrap del body ad eccezion fatta di IntelliJ. Per chi ha familiriatà con i sistemi operativi UNIX-like VIM può in questo caso diventare il vostro migliore amico quando si scrivono messaggi di commit, basterà infatti aggiungere il seguente comando all'interno del file .vimrc "**au FileType gitcommit set tw=72**" che farà si che il vostro corpo della commit vada a capo ogni 72 caratteri.


### 7. Usare il corpo della commit per spiegare cosa e perché invece di come

Questo messaggio di commit del [Core Bitcon](https://github.com/bitcoin/bitcoin/commit/eb0b56b19017ab5c16c745e6da39c53126924ed6) è un'ottimo esempio:
> commit eb0b56b19017ab5c16c745e6da39c53126924ed6
> Author: Pieter Wuille <pieter.wuille@gmail.com>
> Date:   Fri Aug 1 22:57:55 2014 +0200
> 
>   Simplify serialize.h's exception handling
>
>   Remove the 'state' and 'exceptmask' from serialize.h's stream
   implementations, as well as related methods.
>
>   As exceptmask always included 'failbit', and setstate was always
   called with bits = failbit, all it did was immediately raise an
   exception. Get rid of those variables, and replace the setstate
   with direct exception throwing (which also removes some dead
   code).
>
>   As a result, good() is never reached after a failure (there are
   only 2 calls, one of which is in tests), and can just be replaced
   by !eof().
>
>   fail(), clear(n) and exceptions() are just never called. Delete
   them.

Notiamo come l'autore Pieter Wuille abbia usato in maniera eccezionale l'uso del "**cosa**" e "**perché**" all'interno del corpo della commit. In breve ci spiega cosa sollevava l'eccezione e perché si è liberato di determinati metodi presenti all'interno del file serialize.h.

A questo punto il "**come**" se ne è liberato diventerà superfluo. Se proprio interessati gli alri membri del team potranno vedere come ha fatto ciò usando il comando `git diff`.

Ciò che ha fatto Pieter è importantissimo in quanto permetterà agli altri di non commettere errori nel caso ci sia bisogno di effettuare modifiche all'interno della classe. Concentratevi quindi solo sul chiarire i motivi per cui avete apportato il cambiamento in primo luogo, specificate il modo in cui le cose hanno funzionato prima del cambiamento (e cosa c'era di sbagliato in questo) e spiegate il modo in cui funzionano ora e perché avete deciso di risolvere in questa maniera.

### Git commit message emoji

Può essere utile anche se non è richiesto ai fini di un progetto usare all'interno dei messaggi di commit le emoji. Le emoji danno un tocco di stile ai messaggi di commit all'interno di piattaforme che gestiscono repository Git quali Gitlab o GitHub ma possono diventare controproducenti quando si usa git da terminale o attraverso prodotti di terze parti quali Sourcetree in quanto prendono spazio all'oggetto della commit che ricordiamo essere di 50 caratteri. Altra cosa, le emoji non sono visibili su tali client. Inoltre, aggiungere all'inizio dell'oggetto della commit un emoji porta a non rispettare più i punti 3 e 5. Quindi, stabilite sempre con il vostro team di sviluppo quale strada sia meglio intraprendere e ricordate di non fare assolutamente di testa vostra.

### Development

|   Commit type              | Emoji                                         |
|:---------------------------|:----------------------------------------------|
| Initial commit             | :tada: `:tada:`                               |
| New feature                | :sparkles: `:sparkles:`                       |
| Bugfix                     | :bug: `:bug:`                                 |
| Refactor code              | :hammer: `:hammer:`                           |
| Removing code/files        | :fire: `:fire:`                               |
| Removing a dependency      | :heavy_minus_sign: `:heavy_minus_sign:`       |
| Adding a dependency        | :heavy_plus_sign: `:heavy_plus_sign:`         |
| Translation                | :alien: `:alien:`                             |
| Text                       | :pencil: `:pencil:`                           |
| Work in progress           | :construction:  `:construction:`              |
| Accessibility              | :wheelchair: `:wheelchair:`                   |



### Tuning Performance & Architecture

|   Commit type              | Emoji                                         |
|:---------------------------|:----------------------------------------------|
| General update             | :zap: `:zap:`                                 |
| Improve format/structure   | :art: `:art:`                                 |
| Security                   | :lock: `:lock:`                               |
| Upgrading dependencies     | :arrow_up: `:arrow_up:`                       |
| Downgrading dependencies   | :arrow_down: `:arrow_down:`                   |
| Lint                       | :shirt: `:shirt:`                             |


### Documentation

|   Commit type              | Emoji                                         |
|:---------------------------|:----------------------------------------------|
| Version tag                | :bookmark: `:bookmark:`                       |
| Metadata                   | :card_index: `:card_index:`                   |
| Documentation              | :books: `:books:`                             |
| Documenting source code    | :bulb: `:bulb:`                               |
| Bad code / need improv.    | :hankey: `:hankey:`                           |
| Reverting changes          | :rewind: `:rewind:`                           |
| Breaking changes           | :boom: `:boom:`                               |
| Code review changes        | :ok_hand: `:ok_hand:`                         |

### Application Management

|   Commit type              | Emoji                                         |
|:---------------------------|:----------------------------------------------|
| Critical hotfix            | :ambulance: `:ambulance:`                     |
| Deploying stuff            | :rocket: `:rocket:`                           |
| Fixing on MacOS            | :apple: `:apple:`                             |
| Fixing on Linux            | :penguin: `:penguin:`                         |
| Fixing on Windows          | :checkered_flag: `:checkered_flag:`           |


### DevOps

|   Commit type              | Emoji                                         |
|:---------------------------|:----------------------------------------------|
| Performance                | :racehorse: `:racehorse:`                     |
| Cosmetic                   | :lipstick: `:lipstick:`                       |
| Tests                      | :rotating_light: `:rotating_light:`           |
| Adding a test              | :white_check_mark: `:white_check_mark:`       |
| Continuous Integration     | :green_heart: `:green_heart:`                 |
| Adding CI build system     | :construction_worker: `:construction_worker:` |
| Analytics or tracking code | :chart_with_upwards_trend: `:chart_with_upwards_trend:` |
| Docker                     | :whale: `:whale:`                             |
| Configuration files        | :wrench: `:wrench:`                           |
| Merging branches           | :twisted_rightwards_arrows: `:twisted_rightwards_arrows:` |

[Be creative](http://www.emoji-cheat-sheet.com/)

### Conclusione

Bene, siamo arrivati alla fine della guida. Sperando che ciò sia stato di vostro gradimento e soprattutto vi sia stato utile vi ricordiamo e raccomandiamo di usare sempre queste 7 regole per scrivere i messaggi di commit in tutti i vostri progetti di partepazione.
