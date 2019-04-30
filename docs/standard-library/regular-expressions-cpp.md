---
title: Expresiones regulares (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C++, regular expressions
- regular expressions, Visual C++
- regular expressions
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
ms.openlocfilehash: dafbe7c7ba10db2b0f34fdc6065c1475d63be284
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369038"
---
# <a name="regular-expressions-c"></a>Expresiones regulares (C++)

La biblioteca estándar de C++ admite varias gramáticas de expresiones regulares. Este tema describen las variaciones de gramática disponibles al utilizar expresiones regulares.

## <a name="regexgrammar"></a> Gramática de expresiones regulares

La gramática de expresiones regulares para usar al especificado por el uso de uno de los `std::regex_constants::syntax_option_type` valores de enumeración. Estos gramáticas de expresiones regulares se definen en std::regex_constants:

- `ECMAScript`: Esto es más cercana a la gramática usada JavaScript y los lenguajes. NET.
- `basic`: Las expresiones regulares de POSIX básicas o BRE.
- `extended`: El POSIX amplía las expresiones regulares o ERE.
- `awk`: Se trata de `extended`, pero tiene más secuencias de escape para caracteres no imprimibles.
- `grep`: Se trata de `basic`, sino que también permite newline caracteres ('\n') separar alternancias.
- `egrep`: Se trata de `extended`, sino que también permite caracteres de nueva línea separar alternancias.

De forma predeterminada, si no se especifica ninguna gramática, `ECMAScript` se da por hecho. Se puede especificar sólo una gramática.

Además de la gramática, se pueden aplicar varias marcas:
- `icase`: Omitir mayúsculas y minúsculas al comparar.
- `nosubs`: Omitir coincidencias marcadas (es decir, las expresiones entre paréntesis); no se almacenan las sustituciones.
- `optimize`: Asegúrese de coincidencia con mayor rapidez, con el posible costo de mayor tiempo de construcción.
- `collate`: Use secuencias de intercalación de la configuración regional (por ejemplo, los intervalos de la forma "[a-z]").

Cero o más marcadores se pueden combinar con la gramática para especificar el comportamiento del motor de expresiones regulares. Si solo se especifican las marcas, `ECMAScript` se asume que la gramática.

### <a name="element"></a>Elemento

Un elemento puede ser algo de lo siguiente:

- Un *carácter ordinario* que coincide con el mismo carácter en la secuencia de destino.

- Un *carácter comodín* "." que coincide con cualquier carácter de la secuencia de destino excepto una nueva línea.

- Una *expresión entre corchetes* con la forma "[`expr`]", que coincide con un carácter o con un elemento de intercalación en la secuencia de destino que se encuentra también en el conjunto definido por la expresión `expr`, o con la forma "[^`expr`]", que coincide con un carácter o un elemento de intercalación de la secuencia de destino que no está en el conjunto definido por la expresión `expr`.

   La expresión `expr` puede contener cualquier combinación de lo siguiente:

   - Un carácter individual. Agrega ese carácter al conjunto definido por `expr`.

   - Un *intervalo de caracteres* con la forma "`ch1`-`ch2`". Agrega los caracteres representados por valores del intervalo cerrado [`ch1`, `ch2`] al conjunto definido por `expr`.

   - Una *clase de carácter* con la forma "[:`name`:]". Agrega los caracteres de la clase con nombre al conjunto definido por `expr`.

   - Una *clase de equivalencia* con la forma "[=`elt`=]". Agrega los elementos de intercalación que son equivalentes a `elt` al conjunto definido por `expr`.

   - Un *símbolo de intercalación* con la forma "[.`elt`.]". Agrega el elemento de intercalación `elt` al conjunto definido por `expr`.

- Un *delimitador*. El delimitador “^” coincide con el inicio de la secuencia de destino; el delimitador “$” coincide con el final de la secuencia de destino.

Un *grupo de capturas* con la forma "( *subexpresión* )" o "\\( *subexpresión* \\)" en `basic` y `grep`, que coincide con la secuencia de caracteres de la secuencia de destino que coincide con el patrón entre los delimitadores.

- Un *carácter de escape de identidad* con la forma "\\`k`", que coincide con el carácter `k` en la secuencia de destino.

Ejemplos:

- “a” coincide con la secuencia de destino “a” pero no coincide con las secuencias de destino “B”, “b” o “c”.

- “.” coincide con todas las secuencias de destino “a”, “B”, “b” y “c”.

- "[b-z]" coincide con las secuencias de destino "b" y "c" pero no coincide con las secuencias de destino "a" o “B”.

- "[:lower:]" coincide con las secuencias de destino "a", "b" y "c" pero no coincide con la secuencia de destino “B”.

- “(a)” coincide con la secuencia de destino “a” y asocia el grupo de captura 1 con la subsecuencia “a”, pero no coincide con las secuencias de destino “B”, “b” o “c”.

En `ECMAScript`, `basic` y `grep`, un elemento también puede ser una *referencia inversa* con la forma "\\`dd`", donde `dd` representa un valor N decimal que coincide con una secuencia de caracteres de la secuencia de destino, que es igual que la secuencia de caracteres que coincide con el eNésimo *grupo de capturas*. Por ejemplo, “(a) \1” coincide con la secuencia de destino “aa” porque el primer grupo de captura (y único) coincide con la secuencia inicial “a” y, después, el \1 coincide con la secuencia final “a”.

En `ECMAScript`, un elemento también puede ser una de las siguientes cosas:

- Un *grupo de no-captura* del formulario "(?: *subexpresión* )". Coincide con la secuencia de caracteres de la secuencia de destino que coincide con el patrón entre los delimitadores.

- Una *secuencia de escape de caracteres* limitada con la forma "\f", "\n", "\r", "\t" o "\v". Estos coinciden con un avance de página, una nueva línea, un retorno de carro, una tabulación horizontal y una tabulación vertical, respectivamente, en la secuencia de destino.

- Una *aserción positiva* con la forma "(= *subexpresión* )". Coincide con la secuencia de caracteres de la secuencia de destino que coincide con el patrón entre los delimitadores, pero no cambia la posición de coincidencia en la secuencia de destino.

- Una *aserción negativa* con la forma "(! *subexpresión* )". Coincide con cualquier secuencia de caracteres de la secuencia de destino que no coincida con el patrón entre los delimitadores y no cambia la posición de coincidencia en la secuencia de destino.

- Una *secuencia de escape hexadecimal* con la forma "\x`hh`". Coincide con un carácter en la secuencia de destino representado por los dos dígitos hexadecimales `hh`.

- Una *secuencia de escape Unicode* con la forma "\u`hhhh`". Coincide con un carácter de la secuencia de destino representado por los cuatro dígitos hexadecimales `hhhh`.

- Una *secuencia Control Esc* con la forma "\c`k`". Coincide con el carácter de control que denomina el carácter `k`.

- Una *aserción de límite de palabra* con la forma "\b". Coincide cuando la posición actual en la secuencia de destino está inmediatamente después de un *límite de palabra*.

- Una *aserción de límite de palabra negativa* con la forma "\B". Coincide cuando la posición actual en la secuencia de destino no está inmediatamente después de un *límite de palabra*.

- Un *escape de caracteres dsw* con la forma "\d", "\D", "\s", "\S", "\w", "\W". Proporciona un nombre corto para una clase de carácter.

Ejemplos:

- “(?:a)” coincide con la secuencia de destino “a”, pero “(?:a) \1” no es válida porque no hay ningún grupo de captura 1.

- "(=a)a" coincide con la secuencia de destino "a". La aserción positiva coincide con la secuencia inicial “a” en la secuencia de destino y la “a” final de la expresión regular coincide con la secuencia inicial “a” de la secuencia de destino.

- "(!a)a" no coincide con la secuencia de destino "a".

- "a\b." coincide con la secuencia de destino "a~", pero no coincide con la secuencia de destino "ab".

- "a\B." coincide con la secuencia de destino "ab", pero no coincide con la secuencia de destino "a~".

En `awk`, un elemento también puede ser una de las siguientes cosas:

- Una *secuencia de escape de caracteres* con la forma "\\\\", "\a", "\b", "\f", "\n", "\r", "\t" o "\v". Estos coinciden con una barra diagonal inversa, una alerta, un retroceso, un avance de página, una nueva línea, un retorno de carro, una tabulación horizontal y una tabulación vertical, respectivamente, en la secuencia de destino.

- Una *secuencia de escape octal* con la forma "\\`ooo`". Coincide con un carácter en la secuencia de destino cuya representación es el valor representado por uno, dos o tres de los dígitos octales `ooo`.

### <a name="repetition"></a>Repetición

Cualquier elemento que no sea una *aserción positiva*, una *aserción negativa* o un *delimitador* puede ir seguido de un recuento de repetición. La forma más general de recuento de repetición adopta la forma "{`min`,`max`}" o "\\{`min`,`max`\\}" en `basic` y `grep`. Un elemento al que sigue esta forma de recuento de repetición coincide al menos con las sucesivas repeticiones de `min` y no más que las sucesivas repeticiones de `max` de una secuencia que coincide con el elemento. Por ejemplo, "un{2,3}" coincide con la secuencia de destino "aa" y la secuencia de destino "aaa", pero no la secuencia de destino "a" o la secuencia de destino "aaaa".

Un recuento de repetición también puede adoptar una de las siguientes formas:

- "{`min`}" o "\\{`min`\\}" en `basic` y `grep`. Equivalente a "{`min`,`min`}".

- "{`min`,}" o "\\{`min`,\\}" en `basic` y `grep`. Equivalente a “{`min`,unbounded}”.

- "\*". Equivalente a "{0,unbounded}”.

Ejemplos:

- "un{2}" coincide con la secuencia de destino "aa", pero no la secuencia de destino "a" o la secuencia de destino "aaa".

- "un{2,}" coincide con la secuencia de destino "aa", la secuencia de destino "aaa" etc., pero no coincide con la secuencia de destino "a".

- "un\*" coincide con la secuencia de destino "", el destino de secuencia "a", la secuencia de destino "aa" y así sucesivamente.

En todas las gramáticas excepto `basic` y `grep`, un recuento de repetición también puede adoptar una de las siguientes formas:

- "?". Equivalente a "{0,1}".

- "+". Equivalente a "{1,unbounded}".

Ejemplos:

- ¿"a"? coincide con la secuencia de destino "" y la secuencia de destino "a", pero no la secuencia de destino "aa".

- "a+" coincide con las secuencias de destino “a” y "aa", etcétera, pero no con la secuencia de destino "".

En `ECMAScript`, todos los formularios de recuento de repetición pueden ir seguidos por el carácter '?', que designa un *repetición no expansiva*.

### <a name="concatenation"></a>Concatenación

Los elementos de expresión regular, con o sin *recuentos de repetición*, se pueden concatenar para formar expresiones regulares más largas. La expresión resultante coincide con una secuencia de destino que es una concatenación de las secuencias que coinciden con los elementos individuales. Por ejemplo, "un{2,3}b" coincide con la secuencia de destino "aab" y la secuencia de destino "aaab", pero no coincide con las secuencias de destino "ab" o la secuencia de destino "aaaab".

### <a name="alternation"></a>Alternancia

En todas las gramáticas de expresiones regulares con excepción de `basic` y `grep`, una expresión regular concatenada puede ir seguida del carácter "&#124;" y otra expresión regular concatenada. Cualquier cantidad de expresiones regulares concatenadas se pueden combinar de esta manera. La expresión resultante coincide con cualquier secuencia de destino que coincida con una o más de las expresiones regulares concatenadas.

Cuando más de una de las expresiones regulares concatenadas coincide con la secuencia de destino, `ECMAScript` elige como la coincidencia la primera de las expresiones regulares concatenadas que coincide con la secuencia (*primera coincidencia*); el resto de las gramáticas de expresiones regulares eligen la que alcanza la *coincidencia más larga*. Por ejemplo, "ab&#124;cd" coincide con las secuencias de destino "ab" y "cb", pero no coincide con las secuencias de destino "abd" ni "acd".

En `grep` y `egrep`, un carácter de nueva línea (“\n ") se puede utilizar para separar alternancias.

### <a name="subexpression"></a>Subexpression

En `basic` y `grep`, una subexpresión es una concatenación. En el resto de las gramáticas de expresiones regulares, una subexpresión es una alternancia.

## <a name="grammarsummary"></a> Resumen de la gramática

En la siguiente tabla se resumen las características que están disponibles en las diferentes gramáticas de expresiones regulares:

|Elemento|básicos|extendidos|ECMAScript|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|alternancia usando "&#124;"||+|+||+|+|
|alternancia usando '\n'||||+|+||
|delimitador|+|+|+|+|+|+|
|referencia inversa|+||+|+|||
|expresión entre corchetes|+|+|+|+|+|+|
|grupo de captura usando "()”||+|+||+|+|
|grupo de captura usando "\\(\\)"|+|||+|||
|secuencia de escape de control|||+||||
|carácter de escape dsw|||+||||
|escape de formato de archivo|||+|||+|
|secuencia de escape hexadecimal|||+||||
|escape de identidad|+|+|+|+|+|+|
|aserción negativa|||+||||
|aserción de límite de palabra negativa|||+||||
|grupo de no-captura|||+||||
|repetición no expansiva|||+||||
|secuencia de escape octal||||||+|
|caracteres ordinarios|+|+|+|+|+|+|
|aserción positiva|||+||||
|repetición usando "{}"||+|+||+|+|
|repetición usando "\\{\\}"|+|||+|||
|repetición usando '\*'|+|+|+|+|+|+|
|repetición usando “?” y “+”||+|+||+|+|
|secuencia de escape Unicode|||+||||
|carácter comodín|+|+|+|+|+|+|
|aserción de límite de palabra|||+||||

## <a name="semanticdetails"></a> Detalles semánticos

### <a name="anchor"></a>Delimitador

Un delimitador coincide con una posición de la cadena de destino, no con un carácter. Un carácter “^” coincide con el principio de la cadena de destino y “$” coincide con el final de la cadena de destino.

### <a name="back-reference"></a>Referencia inversa

Una referencia inversa es una barra diagonal inversa seguida de un valor decimal N. Coincide con el contenido del eNésimo *grupo de capturas*. El valor de N no debe ser mayor que el número de grupos de captura que preceden a la referencia inversa. En `basic` y `grep`, el valor de N lo determina el dígito decimal que sigue a la barra diagonal inversa. En `ECMAScript`, el valor de N viene determinado por todos los dígitos decimales que siguen inmediatamente a la barra diagonal inversa. Por consiguiente, en `basic` y `grep`, el valor de N nunca es mayor que 9, aunque la expresión regular tenga más de nueve grupos de captura. En `ECMAScript`, el valor de N es unbounded.

Ejemplos:

- “((a+) (b+))(c+) \3” coincide con la secuencia de destino “aabbbcbbb”. La referencia inversa “\3” coincide con el texto del tercer grupo de captura, es decir, “(b+)”. No coincide con la secuencia de destino “aabbbcbb”.

- "(a)\2" no es válido.

- “(b (((((((((a))))))))))\10” tiene significados diferentes en `basic` y en `ECMAScript`. En `basic` la referencia inversa es "\1". La referencia inversa coincide con el contenido del primer grupo de captura (es decir, el que comienza con “(b” y finaliza con el cierre ")” y va antes de la referencia inversa), y el “0 " final coincide con el carácter ordinario “0". En `ECMAScript`, la referencia inversa es "\10". Coincide con el décimo grupo de captura, es decir, el más profundo.

### <a name="bracket-expression"></a>Expresión entre corchetes

Una expresión entre corchetes define un conjunto de caracteres y los *elementos de intercalación*. Cuando la expresión entre corchetes comienza con el carácter “^”, se produce la coincidencia correctamente si ningún elemento del conjunto coincide con el carácter actual en la secuencia de destino. Si no, se produce la coincidencia si alguno de los elementos del conjunto coincide con el carácter actual en la secuencia de destino.

El conjunto de caracteres puede definirse enumerando cualquier combinación de *caracteres individuales*, *intervalos de caracteres*, *clases de caracteres*, *clases de equivalencia* y *símbolos de intercalación*.

### <a name="capture-group"></a>Grupo de captura

Un grupo de captura marca su contenido como una sola unidad en la gramática de expresiones regulares y etiqueta el texto de destino que coincide con su contenido. La etiqueta asociada a cada grupo de captura es un número, que se determina contando los paréntesis de apertura que marcan los grupos de captura e incluyendo el paréntesis de apertura que marca el grupo de captura actual. En esta implementación, el número máximo de grupos de captura es 31.

Ejemplos:

- "ab+" coincide con la secuencia de destino "abb", pero no coincide con la secuencia de destino "abab".

- "(ab)+" no coincide con la secuencia de destino "abb", pero coincide con la secuencia de destino "abab".

- “((a+) (b+))(c+)” coincide con la secuencia de destino “aabbbc” y asocia el grupo de captura 1 con la subsecuencia “aabbb”, el grupo de captura 2 con la subsecuencia “aa”, el grupo de captura 3 con “bbb” y el grupo de captura 4 con la subsecuencia “c”.

### <a name="character-class"></a>Clase de carácter

Una clase de caracteres en una expresión entre corchetes agrega todos los caracteres de la clase con nombre al conjunto de caracteres definido por la expresión entre corchetes. Para crear una clase de caracteres, use “[:” seguido del nombre de la clase seguido de “:]”. Internamente, los nombres de las clases de caracteres se reconocen llamando a `id = traits.lookup_classname`. Un carácter `ch` pertenece a una clase de esas si `traits.isctype(ch, id)` devuelve true. La plantilla `regex_traits` predeterminada admite los nombres de clase incluidos en la tabla siguiente.

|Nombre de clase|Descripción|
|----------------|-----------------|
|“alnum”|letras minúsculas, mayúsculas y dígitos|
|"alpha"|letras minúsculas y mayúsculas|
|"blank"|espacio o tabulación|
|"cntrl"|los caracteres de *escape de formato de archivo*|
|"digit"|dígitos|
|"graph"|letras minúsculas, mayúsculas, dígitos y signos de puntuación|
|"lower"|letras minúsculas|
|"print"|letras minúsculas, mayúsculas, dígitos, signos de puntuación y espacios|
|"punct"|punctuation|
|"space"|espacio|
|"upper|caracteres en mayúsculas|
|"xdigit"|dígitos, “a”, “b”, “c”, “d”, “e”, “f”, “A”, “b”, “C”, “d”, “E”, “f”|
|"d"|igual que dígito|
|"s"|igual que espacio|
|"w"|igual que alnum|

### <a name="character-range"></a>Intervalo de caracteres

Un intervalo de caracteres en una expresión entre corchetes agrega todos los caracteres del intervalo al conjunto de caracteres definido por la expresión entre corchetes. Para crear un intervalo de caracteres, hay que poner el carácter “-” entre el primero y el último carácter del intervalo. Al hacer esto, se incluyen en el conjunto todos los caracteres que tienen un valor numérico mayor o igual que el valor numérico del primer carácter, e igual o menor que el valor numérico del último carácter. Observe que este conjunto de caracteres agregados depende de la representación de caracteres específica de la plataforma. Si el carácter “-” aparece al principio o al final de una expresión entre corchetes, o como el primero o el último carácter de un intervalo de caracteres, se representa a sí mismo.

Ejemplos:

- “[0-7]” representa el conjunto de caracteres { '0', '1', '2', '3', '4', '5', '6', '7' }. Coincide con las secuencias de destino “0 ", “1 ", etcétera, pero no con “a”.

- En los sistemas que utilizan la codificación de caracteres ASCII, "[h-k]" representa el conjunto de caracteres { 'h', 'i', 'j', 'k' }. Coincide con las secuencias de destino "h", "i", etcétera, pero no con "\x8A" ni "0".

- En los sistemas que utilizan la codificación de caracteres EBCDIC, "[h-k]" representa el conjunto de caracteres { "h", "i", "\x8A", "\x8B", "\x8C", "\x8D", "\x8E", "\x8F", "\x90", "j, "k" } ("h" se codifica como 0x88 y "k" como 0x92) Coincide con las secuencias de destino "h", "i", "\x8A", etcétera, pero no con "0".

- "[-0-24]" representa el conjunto de caracteres { "-", "0", "1", "2", "4" }.

- "[0-2-]" representa el conjunto de caracteres { "0", "1", "2", "-" }.

- En los sistemas que utilizan la codificación de caracteres ASCII, "[+--]" representa el conjunto de caracteres { "+", ",", "-" }.

Sin embargo, cuando se utilizan intervalos que distinguen la configuración regional, los caracteres de un intervalo están determinados por las reglas de intercalación de la configuración regional. Los caracteres que se intercalan después del primer carácter y antes del último carácter de la definición del intervalo están en el conjunto. Los dos caracteres finales también están en el conjunto.

### <a name="collating-element"></a>Elemento de intercalación

Un elemento de intercalación es una secuencia de varios caracteres que se interpreta como un único carácter.

### <a name="collating-symbol"></a>Símbolo de intercalación

Un símbolo de intercalación en una expresión entre corchetes agrega un *elemento de intercalación* al conjunto definido por la expresión entre corchetes. Para crear un símbolo de intercalación, use "[." seguido del elemento de intercalación seguido de "."].

### <a name="control-escape-sequence"></a>Secuencia de escape de control

Una secuencia de escape de control es una barra diagonal inversa seguida de la letra “c” seguida de una de las letras de la ”a" a la “z” o de la “A” a la “Z”. Coincide con el carácter de control ASCII al que da nombre esa letra. Por ejemplo, "\ci" coincide con la secuencia de destino "\x09", porque \<ctrl-i> tiene el valor 0x09.

### <a name="dsw-character-escape"></a>Escape de carácter DSW

Un escape de carácter dsw es un nombre corto para una clase de caracteres, como se muestra en la tabla siguiente.

|Secuencia de escape|Clase con nombre equivalente|Clase con nombre predeterminada|
|---------------------|----------------------------|-------------------------|
|"\d"|"[[:d:]]"|"[[:digit:]]"|
|"\D"|"[^[:d:]]"|"[^[:digit:]]"|
|"\s"|"[[:s:]]"|"[[:space:]]"|
|"\S"|"[^[:s:]]"|"[^[:space:]]"|
|"\w"|"[[:w:]]"|"[a-zA-Z0-9_]"\*|
|"\W"|"[^[:w:]]"|"[^a-zA-Z0-9_]"\*|

\*Juego de caracteres ASCII

### <a name="equivalence-class"></a>Clase de equivalencia

Una clase de equivalencia en una expresión entre corchetes agrega todos los caracteres y los *elementos de intercalación* que son equivalentes al elemento de intercalación de la definición de clase de equivalencia al conjunto definido por la expresión entre corchetes. Para crear una clase de equivalencia, se usa “[=” seguido de un elemento de intercalación seguido de “=]”. Internamente, dos elementos de intercalación `elt1` y `elt2` son equivalentes si `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`.

### <a name="file-format-escape"></a>Escape de formato de archivo

Una secuencia de escape de formato de archivo consta de las secuencias de escape habituales de los caracteres del lenguaje C, "\\\\", "\a", "\b", "\f", "\n", "\r", "\t", "\v". Estos tienen los significados usuales, es decir, barra diagonal inversa, alerta, retroceso, avance de página, nueva línea, retorno de carro, tabulación horizontal y tabulación vertical, respectivamente. En `ECMAScript`, "\a" y "\b" no se permiten. (Se permite "\\\\", pero es un carácter de escape de identidad, no una secuencia de escape de caracteres).

### <a name="hexadecimal-escape-sequence"></a>Secuencia de escape hexadecimal

Una secuencia de escape hexadecimal es una barra diagonal inversa seguida de la letra "x", seguida de dos dígitos hexadecimales (0-9a-fA-F). Coincide con un carácter de la secuencia de destino que tiene el valor especificado por los dos dígitos. Por ejemplo, “\x41” coincide con la secuencia de destino “A” cuando se usa la codificación de caracteres ASCII.

### <a name="identity-escape"></a>Escape de identidad

Un escape de identidad es una barra diagonal inversa seguida de un único carácter. Coincide con ese carácter. Se requiere cuando el carácter tiene un significado especial; mediante el escape de identidad, se quita el significado especial. Por ejemplo:

- "un\*" coincide con la secuencia de destino "aaa", pero no coincide con la secuencia de destino "un\*".

- "un\\\*" no coincide con la secuencia de destino "aaa", pero coincide con la secuencia de destino "un\*".

El conjunto de caracteres que se permite en un escape de identidad depende de la gramática de expresiones regulares, como se muestra en la tabla siguiente.

|Gramática|Caracteres de escape de identidad permitidos|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|{ '(', ')', '{', '.', '[', '\\', '\*', '^', '$', '+', '?', '&#124;' }|
|`awk`|`extended` plus { '"', '/' }|
|`ECMAScript`|Todos los caracteres excepto los que pueden formar parte de un identificador. Normalmente, esto incluye letras, dígitos, '$', '\_' y las secuencias de escape unicode. Para obtener más información, vea la Especificación del lenguaje ECMAScript.|

### <a name="individual-character"></a>Carácter individual

Un carácter individual en una expresión entre corchetes agrega ese carácter al conjunto de caracteres definido por la expresión entre corchetes. En cualquier parte de una expresión entre corchetes excepto al principio, un carácter “^” se representa a sí mismo.

Ejemplos:

- “[abc]” coincide con las secuencias de destino “a”, “b”, y “c”, pero no con “d”.

- “[^abc]” coincide con la secuencia de destino “d”, pero no con “a” “b” o “c”.

- “[a^bc]” coincide con las secuencias de destino "a", "b", "c" y "^", pero no con “d”.

En todas las gramáticas de expresiones regulares excepto en `ECMAScript`, si un carácter “]” es el primero que sigue a la apertura “[” o el primero que sigue a un carácter “^ inicial”, se representa a sí mismo.

Ejemplos:

- “[]” no es válido porque no hay ningún carácter “]” que finalice la expresión entre corchetes.

- "[]abc]" coincide con las secuencias de destino "a", "b", "c" y "]", pero no con “d”.

- "[^]abc]" coincide con la secuencia de destino “d”, pero no con "a", "b", "c" o "]".

En `ECMAScript`, se usa "\\]" para representar el carácter "]" en una expresión entre corchetes.

Ejemplos:

- "[]a" coincide con la secuencia de destino “a” porque la expresión entre corchetes está vacía.

- "[\\]abc]" coincide con las secuencias de destino "a", "b", "c" y "]", pero no con "d".

### <a name="negative-assert"></a>Aserción negativa

Una aserción negativa coincide con todo menos con su contenido. No consume ningún carácter de la secuencia de destino. Por ejemplo, "(!aa) (una\*)" coincide con la secuencia de destino "a" y asocia el grupo 1 de captura con la subsecuencia "a". No coincide con la secuencia de destino “aa” ni con la secuencia de destino “aaa”.

### <a name="negative-word-boundary-assert"></a>Aserción de límite de palabra negativa

Una aserción de límite de palabra negativa coincide si la posición actual en la cadena de destino no está inmediatamente después de un *límite de palabra*.

### <a name="non-capture-group"></a>Grupo de no-captura

Un grupo de no-captura marca su contenido como una sola unidad en la gramática de expresiones regulares, pero no etiqueta el texto de destino. Por ejemplo, "(a)(?:b)\*(c)" coincide con el texto de destino "abbc" y asocia el grupo de captura 1 con la subsecuencia "un"y grupo de captura 2 con la subsecuencia "c".

### <a name="non-greedy-repetition"></a>Repetición no expansiva

Una repetición no expansiva usa la subsecuencia más corta de la secuencia de destino que coincida con el patrón. Una repetición expansiva usa la más larga. Por ejemplo, "(a+) (un\*b)" coincide con la secuencia de destino "aaab". Cuando se utiliza una repetición no expansiva, esta asocia el grupo de captura 1 con la subsecuencia “a” al principio de la secuencia de destino y el grupo de destino 2 con la subsecuencia “aab” al final de la secuencia de destino. Cuando se utiliza una coincidencia expansiva, esta asocia el grupo de captura 1 con la subsecuencia “aaa” y el grupo de captura 2 con la subsecuencia “b”.

### <a name="octal-escape-sequence"></a>Secuencia de escape octal

Una secuencia de escape octal es una barra diagonal inversa seguida de uno, dos o tres dígitos octales (0-7). Coincide con un carácter de la secuencia de destino que tiene el valor especificado por esos dígitos. Si todos los dígitos son “0 ", la secuencia no es válida. Por ejemplo, “\101” coincide con la secuencia de destino “A” cuando se usa la codificación de caracteres ASCII.

### <a name="ordinary-character"></a>Caracteres ordinarios

Un carácter ordinario es cualquier carácter válido que no tiene ningún significado especial en la gramática actual.

En `ECMAScript`, los caracteres siguientes tienen significados especiales:

- ^  $  \  .  \*  +  ?  (  )  \[  ]  {  }  &#124;

En `basic` y `grep`, los caracteres siguientes tienen significados especiales:

- .   \[   \

También en `basic` y `grep`, los caracteres siguientes tienen significados especiales cuando se utilizan en un contexto determinado:

- '\*' tiene un significado especial en todos los casos excepto cuando es el primer carácter en una expresión regular o el primer carácter que sigue un inicial ' ^' en una expresión regular, o cuando es el primer carácter de una captura de grupo o el primer carácter que sigue un inicial ' ^' en un grupo de capturas.

- “^” tiene un significado especial cuando es el primer carácter de una expresión regular.

- “$” tiene un significado especial cuando es el último carácter de una expresión regular.

En `extended` y `egrep` y `awk`, los caracteres siguientes tienen significados especiales:

- .   \[   \   (   \*   +   ?   {   &#124;

También en `extended` y `egrep` y `awk`, los caracteres siguientes tienen significados especiales cuando se utilizan en un contexto determinado:

- ")” tiene un significado especial cuando coincide con un carácter “(” precedente.

- “^” tiene un significado especial cuando es el primer carácter de una expresión regular.

- “$” tiene un significado especial cuando es el último carácter de una expresión regular.

Un carácter ordinario coincide con el mismo carácter en la secuencia de destino. De forma predeterminada, esto significa que se produce la coincidencia si los dos caracteres se representan mediante el mismo valor. En una coincidencia sin distinción entre mayúsculas y minúsculas, dos caracteres `ch0` y `ch1` coinciden si `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`. En una coincidencia que distingue la configuración regional, dos caracteres `ch0` y `ch1` coinciden si `traits.translate(ch0) == traits.translate(ch1)`.

### <a name="positive-assert"></a>Aserción positiva

Una aserción positiva coincide con su contenido, pero no utiliza ningún carácter de la secuencia de destino.

Ejemplos:

- "(=AA) (una\*)" coincide con la secuencia de destino "aaaa" y asocia el grupo de captura 1 con la subsecuencia "aaaa".

- "(aa) (un\*)" coincide con la secuencia de destino "aaaa" y asocia el grupo de captura 1 con la subsecuencia "aa" al principio de la secuencia y captura de grupo de destino 2 con la subsecuencia "aa" al final de la secuencia de destino.

- "(=aa)(a)&#124;(a)" coincide con la secuencia de destino "a" y asocia el grupo de capturas 1 con una secuencia vacía (porque se produjo un error en la aserción positiva) y el grupo de capturas 2 con la subsecuencia "a". También coincide con la secuencia de destino “aa” y asocia el grupo de captura 1 con la subsecuencia “aa” y el grupo de captura 2 con una secuencia vacía.

### <a name="unicode-escape-sequence"></a>Secuencia de escape Unicode

Una secuencia de escape unicode es una barra diagonal inversa seguida de la letra "u", seguida de cuatro dígitos hexadecimales (0-9a-fA-F). Coincide con un carácter de la secuencia de destino que tiene el valor especificado por los cuatro dígitos. Por ejemplo, "\u0041" coincide con la secuencia de destino “A” cuando se usa la codificación de caracteres ASCII.

### <a name="wildcard-character"></a>Carácter comodín

Un carácter comodín coincide con cualquier carácter de la expresión de destino excepto con una nueva línea.

### <a name="word-boundary"></a>Límite de palabra

Un límite de palabra aparece en las situaciones siguientes:

- El carácter actual está al principio de la secuencia de destino y es uno de los caracteres alfabéticos `A-Za-z0-9_.`

- La posición del carácter actual se pasa al final de la secuencia de destino y el último carácter de la secuencia de destino es uno de los caracteres alfabéticos.

- El carácter actual es uno de los caracteres alfabéticos y el carácter precedente no lo es.

- El carácter actual no es uno de los caracteres alfabéticos y el carácter precedente sí lo es.

### <a name="word-boundary-assert"></a>Aserción de límite de palabra

Una aserción de límite de palabra coincide cuando la posición actual en la cadena de destino está inmediatamente después de un *límite de palabra*.

## <a name="matchingandsearching"></a> Coincidencias y búsquedas

Para que una expresión regular coincida con una secuencia de destino, la expresión regular completa debe coincidir con la secuencia de destino completa. Por ejemplo, la expresión regular “bcd” coincide con la secuencia de destino “bcd” pero no coincide con la secuencia de destino “abcd” ni “bcde”.

Para que una búsqueda de expresiones regulares dé resultado, debe haber una subsecuencia en alguna parte de la secuencia de destino que coincida con la expresión regular. La búsqueda encuentra, normalmente, la subsecuencia coincidente situada más a la izquierda.

Ejemplos:

- Una búsqueda de la expresión regular “bcd” en la secuencia de destino “bcd” da resultado correcto y coincide con la secuencia completa. La misma búsqueda en la secuencia de destino “abcd” también da resultado y coincide con los tres últimos caracteres. La misma búsqueda en la secuencia de destino “bcde” también da resultado y coincide con los tres primeros caracteres.

- Una búsqueda de la expresión regular “bcd” en la secuencia de destino “bcdbcd” da resultado y coincide con los tres primeros caracteres.

Si hay más de una subsecuencia que coincida en alguna ubicación en la secuencia de destino, hay dos maneras de elegir el patrón coincidente. La *primera coincidencia* elige la subsecuencia que se encuentra primero cuando coincide la expresión regular. La *coincidencia más larga* elige la subsecuencia más larga entre las que coinciden en esa ubicación. Si hay más de una subsecuencia que tenga la longitud máxima, la coincidencia más larga elige la que se encontró en primer lugar. Por ejemplo, cuando se usa la primera coincidencia, una búsqueda de la expresión regular "b&#124;bc" en la secuencia de destino "abcd" coincide con la subsecuencia "b", porque el término de la izquierda de la alternancia coincide con esa subsecuencia; por tanto, la primera coincidencia no prueba con el término de la derecha de la alternancia. Cuando se utiliza la coincidencia más larga, la misma búsqueda coincide con “bc” porque “bc” es más larga que “b”.

Una coincidencia parcial da resultado si la coincidencia llega al final de la secuencia de destino sin dar error, incluso si no alcanza el final de la expresión regular. Por consiguiente, después de que una coincidencia parcial dé resultado, anexar los caracteres a la secuencia de destino puede causar que una coincidencia parcial posterior dé error. Sin embargo, después de que una coincidencia parcial dé error, anexar los caracteres a la secuencia de destino no puede causar que una coincidencia parcial posterior dé resultado correcto. Por ejemplo, con una coincidencia parcial, “ab” coincide con la secuencia de destino “a” pero no con “ac”.

## <a name="formatflags"></a> Marcas de formato

|Reglas de formato de ECMAScript|Reglas de formato usadas|Texto de sustitución|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|La secuencia de caracteres que coincide con la expresión regular completa (`[match[0].first, match[0].second)`)|
|"$$"||"$"|
||"\\&"|"&"|
|"$\`" (signo de dólar seguido de comilla de atrás) || La secuencia de caracteres que precede a la subsecuencia que coincide con la expresión regular (`[match.prefix().first, match.prefix().second)`)|
|"$'" (signo de dólar seguido de comilla simple de cierre)||La secuencia de caracteres que sigue a la subsecuencia que coincide con la expresión regular (`[match.suffix().first, match.suffix().second)`)|
|"$n"|"\n"|La secuencia de caracteres que coincide con el grupo de captura en la posición `n`, donde `n` es un número entre 0 y 9 (`[match[n].first, match[n].second)`)|
||"\\\n"|"\n"|
|"$nn"||La secuencia de caracteres que coincide con el grupo de captura en la posición `nn`, donde `nn` es un número entre 10 y 99 (`[match[nn].first, match[nn].second)`)|

## <a name="see-also"></a>Vea también

[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)<br/>
