# Java Syntax Highlighter #

> Java Syntax Highlighter is discontinued.

## Menu ##
  * [Themes Demo](https://github.com/cws1989/java-syntax-highlighter/blob/wiki/ThemesDemo.md)
  * [Configurations Demo](https://github.com/cws1989/java-syntax-highlighter/blob/wiki/ConfigurationsDemo.md)
  * [Create New Brush](https://github.com/cws1989/java-syntax-highlighter/blob/wiki/CreateNewBrush.md)
  * [Create New Theme](https://github.com/cws1989/java-syntax-highlighter/blob/wiki/CreateNewTheme.md)
  * [Use the Parser Alone](https://github.com/cws1989/java-syntax-highlighter/blob/wiki/UseTheParserAlone.md)

## Overview ##
This library is a java port of [SyntaxHighlighter](http://alexgorbatchev.com/SyntaxHighlighter), the current version ported is 3.0.83. The copyright holder of the
SyntaxHighlighter is Alex Gorbatchev. It is dual licensed under the [MIT](http://www.opensource.org/licenses/MIT) and
[LGPL](http://www.opensource.org/licenses/lgpl-3.0) licenses. This port is written by Chan Wai Shing (cws1989@gmail.com) distributed under
the [MIT](http://www.opensource.org/licenses/MIT) and [LGPL](http://www.opensource.org/licenses/lgpl-3.0) licenses.

  * If you need an editor more than a highlighter, please find [jsyntaxpane](https://github.com/nordfalk/jsyntaxpane).
  * I port it for [Language Files Tool](https://github.com/cws1989/language-files-tool).

## Alternatives ##
[Java Prettify](https://github.com/cws1989/java-prettify)

## Requirement ##
Java SE 6 or up

## Language Supported (Brushes) ##
ActionScript3, Bash/shell, ColdFusion, C#, C++, CSS, Delphi, Diff, Erlang, Groovy, JavaScript, Java, JavaFX, Perl, PHP, Plain Text, PowerShell, Python, Ruby, Scala, SQL, Visual Basic, XML

http://alexgorbatchev.com/SyntaxHighlighter/manual/brushes/

## Themes ##
Default, Django, Eclipse, Emacs, Fade To Grey, MD Ultra, Midnight, RDark

[Click here to visit the gallery.](https://github.com/cws1989/java-syntax-highlighter/blob/wiki/ThemesDemo.md)

## Configurations ##
  * Allows you to change the first (starting) line number.
  * Allows you to turn gutter with line numbers on and off.
  * Allows you to highlight one or more lines to focus user's attention.
  * Allows you to highlight a mixture of HTML/XML code and a script which is very common in web development.

[Click here for a demo.](https://github.com/cws1989/java-syntax-highlighter/blob/wiki/ConfigurationsDemo.md)

## Example ##
> **Note that this highlighter extends Swing component, so all operations are better be executed inside [Swing dispatching thread](http://en.wikipedia.org/wiki/Event_dispatching_thread).**

```java
import java.io.*;
import java.util.*;
import java.util.logging.*;
import javax.swing.*;
import syntaxhighlight.SyntaxHighlighter;
import syntaxhighlighter.brush.*;
import syntaxhighlighter.SyntaxHighlighterParser;
import syntaxhighlighter.theme.ThemeRDark;

public class Example {

  public static void main(String[] args) {
    SwingUtilities.invokeLater(new Runnable() {

      @Override
      public void run() {
        // the SyntaxHighlighter parser
        SyntaxHighlighterParser parser = new SyntaxHighlighterParser(new BrushXml());
        // turn HTML script on
        parser.setHtmlScript(true);
        // set HTML Script brushes
        parser.setHTMLScriptBrushes(Arrays.asList(new BrushCss(), new BrushJScript(), new BrushPhp()));

        // initialize the highlighter and use RDark theme
        SyntaxHighlighter highlighter = new SyntaxHighlighter(parser, new ThemeRDark());
        // set the line number count from 10 instead of 1
        highlighter.setFirstLine(10);
        // set to highlight line 13, 27, 28, 38, 42, 43 and 53
        highlighter.setHighlightedLineList(Arrays.asList(13, 27, 28, 38, 42, 43, 53));
        try {
          highlighter.setContent(new File("test.html"));
        } catch (IOException ex) {
          Logger.getLogger(Example.class.getName()).log(Level.SEVERE, null, ex);
        }

        JFrame frame = new JFrame();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setContentPane(highlighter);
        frame.setLocationByPlatform(true);
        frame.pack();
        frame.setVisible(true);
      }
    });
  }
}
```

## Sample Screenshot ##
![ThemeDefault](https://raw.githubusercontent.com/cws1989/java-syntax-highlighter/wiki/ThemesDemo/ThemeDefault.png)

## Support & Discussion ##
[Support & Discussion Group](http://groups.google.com/group/java-syntax-highlighter)

## Google Project ##
https://code.google.com/archive/p/java-syntax-highlighter/
