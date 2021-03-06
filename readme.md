<!-- region modline

vim: set tabstop=4 shiftwidth=4 expandtab:
vim: foldmethod=marker foldmarker=region,endregion:

endregion

region header

Copyright Torben Sickert 16.12.2012

License
-------

This library written by Torben Sickert stand under a creative commons naming
3.0 unported license. see http://creativecommons.org/licenses/by/3.0/deed.de

endregion -->

<!--|deDE:Einsatz-->
<!--|frFR:Utilisier-->
Use case
--------

A jQuery plugin to replace alternate version of text for client side
internationalization.
<!--deDE:
    Ein jQuery-Plugin zum klientseitigem Ersetzten von verschiedenen
    Textversionen. Perfekt für die Internationalisierung Ihres Webprojekts.
-->
<!--frFR:
    Un plugin jQuery pour remplacer version alternative de texte pour le côté
    client l'internationalisation.
-->

<!--|deDE:Verwendung-->
<!--|frFR:Demande-->
Usage
-----

To add two versions of a text string you can simply add your translation
directly in markup. See how easy it is:
<!--deDE:
    Um zwei Sprachversionen eines Text Knotens im Markup anzubieten müssen
    einfach nur per Kommentar alternative Versionen hinter dem zu übersetzenden
    String gesetzt werden.
-->
<!--frFR:
    Doit offrir deux versions linguistiques d'un nœud de texte dans la balise
    facile à traduire que par Commentez versions alternatives derrière le
    Chaîne à être réglé.
-->

<!--showExample-->

    #!HTML

    <p>
        Your englisch version.
        <!--deDE:Ihre deutsche Variante.-->
        <!--frFR:
            Sa version française.
        -->
    </p>

Sometime you need to explicit mark a text node as text to replace with next
translation node. In this case you can simple wrap a self defined dom node.
<!--deDE:
    Manchmal muss man Textknoten explizit als übersetzbar markieren, da sie
    beispielsweise selbst aus mehr als nur einem Knoten bestehen. In solchen
    Fällen kann einfach ein selbst definierter DOM-Knoten ummantelt werden.
-->
<!--frFR:
    Parfois, vous devez sélectionner explicitement les nœuds de texte comme
    traduisible, car ils Ainsi, même consister en plus d'un noeud. dans ce Cas
    peuvent être facilement enveloppé d'un noeud DOM auto-défini.
-->

<!--showExample-->

    #!HTML

    <langreplace>
        Your englisch version with <strong>dom nodes</strong> inside.
    </langreplace>
    <!--deDE:
        Ihre deutsche Variante mit eingebetteten <strong>dom Knoten</strong>.
    -->
    <!--frFR:
        Votre version français <strong>dom nodes</strong> à l'intérieur.
    -->

It is also possible to use an alternative replacement node.
<!--deDE:Man kann auch einen alternative Ersetzungsknoten einsetzten.-->
<!--frFR:
    Donc, il est possible d'utiliser alternative à nœud de remplacement.
-->

<!--showExample-->

    #!HTML

    <langreplace>
        Your englisch version with <strong>dom nodes</strong> inside.
    </langreplace>
    <langreplacement>deDE:
        Ihre deutsche Variante mit eingebetteten <strong>dom Knoten</strong>.
    </langreplacement>
    <langreplacement>frFR:
        Votre version français <strong>dom nodes</strong> à l'intérieur.
    </langreplacement>

Usually the language dom node precedes the text node to translate. It is
possible to write a special syntax to use a replacement for the next dom node
containing text.
<!--deDE:
    Normalerweise folgt der Sprach-DOM-Knoten auf den Textknoten der übersetzt
    werden soll. Es ist mit einer speziellen Syntax möglich einen
    Sprach-DOM-Knoten für den darauf folgenden DOM-Knoten anzuwenden.
-->
<!--frFR:
    Normalement, le nœud DOM voix suit le nœud de texte de la traduction
    devrait être. Il est doté d'une syntaxe spéciale possible une Nœud voix Dom
    pour le nœud DOM prochaine à utiliser.
-->

<!--showExample-->

    #!HTML

    <!--|deDE:Ihre deutsche Variante.--><!--|frFR:Votre version français.-->
    <p>Your englisch version.</p>

Its possible to save one translation once if you specify the area with known
translations.
<!--deDE:
    Es ist möglich eine Übersetzung an nur einem Ort zu speichern, sofern der
    Bereich mit bekannten Übersetzungen markiert wird.
-->
<!--frFR:
    Il est possible d'enregistrer une traduction en un seul endroit, à moins
    que le Région est marquée avec des traductions connues.
-->

<!--showExample-->

    #!HTML

    <!--The "div.toc" selector defines the default known language area.-->
    <div class="toc">
      <ul>
        <li><a href="title-1">title 1</a></li>
          <ul>
            <li><a href="title-2">title 2</a></li>
          </ul>
      </ul>
    </div>
    <h1 id="title-1">title 1<!--deDE:Titel 1--><!--frFR:titre 1--></h1>
    <h2 id="title-2">title 2<!--deDE:Titel 2--><!--frFR:titre 2--></h2>

With the below initialisation you can simple add this links everywhere in your
page to switch language. On click you will switch the current language
interactively. Try it by yourself:
<!--deDE:
    Mit der unten aufgezeigten Konfiguration können Sie einfach folgenden Links
    an beliebiger Stelle im Markup plazieren. Beim Klicken auf die
    Sprach-Wechsel-Links wird die Sprache Ihrer Webseite entsprechend
    angepasst. Versuchen Sie selbst:
-->
<!--frFR:
    Avec la configuration au-dessous, vous pouvez simplement identifié les
    liens suivants placer n'importe où dans le balisage. Lorsque vous cliquez
    sur l' Langue échange de liens est la langue de votre site en conséquence
    ajustée. Essayez par vous-même:
-->

<!--showExample-->

    #!HTML

    <a href="#lang-deDE">de</a>
    <a href="#lang-enUS">en</a>
    <a href="#lang-frFR">fr</a>

Here you can see a complete initialisation example with all available options
to initialize the plugin with different configuration.
<!--deDE:
    Hier können Sie ein Komplettbeispiel der Initialisierung sehen und alle
    verfügbaren Optionen betrachten, um das Plugin in verschiedenen
    Konfigurationen zu verwenden.
-->
<!--frFR:
    Ici vous pouvez voir toutes les options disponibles pour le plug-in
    différentes configurations pour initialiser.
-->

    #!HTML

    <script type="text/javascript" src="distributionBundle/jquery-2.1.0.js"></script>
    <script type="text/javascript" src="distributionBundle/jquery-tools-1.0.js"></script>
    <script type="text/javascript" src="distributionBundle/jquery-lang-1.0.js"></script>
    <script type="text/javascript">
        $(function($) {
            $.Lang({
                domNodeSelectorPrefix: 'body',
                default: 'enUS',
                domNodeClassPrefix: '',
                templateDelimiter: {
                    pre: '{{',
                    post: '}}'
                },
                fadeEffect: true,
                textNodeParent: {
                    fadeIn: {duration: 'fast'},
                    fadeOut: {duration: 'fast']
                },
                preReplacementLanguagePattern: '^\\|({1})$',
                replacementLanguagePattern: '^([a-z]{2}[A-Z]{2}):((.|\\s)*)$',
                currentLanguagePattern: '^[a-z]{2}[A-Z]{2}$',
                replacementDomNodeName: ['#comment', 'langreplacement'],
                replaceDomNodeNames: ['#text', 'langreplace'],
                toolsLockDescription: '{1}Switch',
                languageHashPrefix: 'lang-',
                currentLanguageIndicatorClassName: 'current',
                cookieDescription: '{1}Last',
                languageMapping: {
                    deDE: ['de', 'de-de', 'german', 'deutsch'],
                    enUS: ['en', 'en-us'],
                    enEN: ['en-en', 'english'],
                    frFR: ['fr', 'fr-fr', 'french']
                }
                onSwitched: $.noop(),
                onSwitch: $.noop(),
                domNode: {knownLanguage: 'div.toc'}
            });
        });
    </script>
