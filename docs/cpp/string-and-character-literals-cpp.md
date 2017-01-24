---
title: "Literales de cadena y car&#225;cter (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "R"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "secuencias de escape"
  - "L (constante)"
  - "cadenas literales"
  - "cadenas literales, C++"
  - "cadenas null"
  - "cadenas null, cadenas terminadas en null"
  - "NULL, constante de carácter"
  - "literales de cadena"
  - "literales de cadena, sintaxis"
  - "cadenas [C++], literales de cadena"
  - "caracteres anchos, cadenas"
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
caps.latest.revision: 36
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Literales de cadena y car&#225;cter (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ admite varios tipos de cadenas y caracteres, y proporciona maneras de expresar valores literales de cada uno de esos tipos. En el código fuente, el contenido de los literales de carácter y cadena se expresa mediante un juego de caracteres. Los nombres de carácter universal y los caracteres de escape permiten expresar cualquier cadena con tan solo el juego básico de caracteres de código fuente. Un literal de cadena sin formato permite evitar la utilización de caracteres de escape y puede usarse para expresar todos los tipos de literales de cadena. También se pueden crear literales std::string sin necesidad de seguir pasos adicionales de construcción o conversión.  
  
```cpp  
#include <string> using namespace std::string_literals; // enables s-suffix for std::string literals int main() { // Character literals auto c0 =   'A'; // char auto c1 = u8'A'; // char auto c2 =  L'A'; // wchar_t auto c3 =  u'A'; // char16_t auto c4 =  U'A'; // char32_t // String literals auto s0 =   "hello"; // const char* auto s1 = u8"hello"; // const char*, encoded as UTF-8 auto s2 =  L"hello"; // const wchar_t* auto s3 =  u"hello"; // const char16_t*, encoded as UTF-16 auto s4 =  U"hello"; // const char32_t*, encoded as UTF-32 // Raw string literals containing unescaped \ and " auto R0 =   R"("Hello \ world")"; // const char* auto R1 = u8R"("Hello \ world")"; // const char*, encoded as UTF-8 auto R2 =  LR"("Hello \ world")"; // const wchar_t* auto R3 =  uR"("Hello \ world")"; // const char16_t*, encoded as UTF-16 auto R4 =  UR"("Hello \ world")"; // const char32_t*, encoded as UTF-32 // Combining string literals with standard s-suffix auto S0 =   "hello"s; // std::string auto S1 = u8"hello"s; // std::string auto S2 =  L"hello"s; // std::wstring auto S3 =  u"hello"s; // std::u16string auto S4 =  U"hello"s; // std::u32string // Combining raw string literals with standard s-suffix auto S5 =   R"("Hello \ world")"s; // std::string from a raw const char* auto S6 = u8R"("Hello \ world")"s; // std::string from a raw const char*, encoded as UTF-8 auto S7 =  LR"("Hello \ world")"s; // std::wstring from a raw const wchar_t* auto S8 =  uR"("Hello \ world")"s; // std::u16string from a raw const char16_t*, encoded as UTF-16 auto S9 =  UR"("Hello \ world")"s; // std::u32string from a raw const char32_t*, encoded as UTF-32 }  
```  
  
 Los literales de cadena no tienen prefijos o tienen los prefijos `u8`, `L`, `u` y `U` para denotar caracteres estrechos \(byte único o multibyte\), UTF\-8, caracteres anchos \(UCS\-2 o UTF\-16\), codificaciones UTF\-16 y UTF\-32, respectivamente. Un literal de cadena sin formato puede tener los prefijos `R`, `u8R`, `LR`, `uR` y `UR` para los equivalentes sin formato de estas codificaciones  Para crear valores std::string temporales o estáticos, puede usar literales de cadena o literales de cadena sin formato con un sufijo `s`. Para obtener más información, consulte la sección Literales de cadena a continuación. Para obtener más información sobre el juego básico de caracteres de código fuente, los nombres de carácter universal y el uso de caracteres para páginas de códigos extendidas en el código fuente, consulte [Juegos de caracteres](../cpp/character-sets2.md).  
  
## Literales de carácter  
 Un *literal de carácter* está compuesto por un carácter de constante. Se representa mediante el carácter delimitado por comillas simples. Hay cuatro tipos de literales de carácter:  
  
-   Literales de caracteres estrechos de tipo `char` \(por ejemplo, `'a'`\)  
  
-   Literales de caracteres anchos de tipo `wchar_t` \(por ejemplo, `L'a'`\)  
  
-   Literales de caracteres anchos de tipo `char16_t` \(por ejemplo, `u'a'`\)  
  
-   Literales de caracteres anchos de tipo `char32_t` \(por ejemplo, `U'a'`\)  
  
 El carácter que se usa para un literal de carácter puede ser cualquier carácter, a excepción de los caracteres reservados como la barra diagonal inversa \(\\\), las comillas simples \('\) o la nueva línea \(\\n\). Los caracteres reservados se pueden especificar mediante una secuencia de escape. Los caracteres se pueden especificar mediante nombres de carácter universal, siempre que el tipo sea lo suficientemente grande como para contener al carácter.  
  
###  <a name="bkmk_Escape"></a> Secuencias de escape  
 Hay tres tipos de secuencias de escape: simple, octal, hexadecimal. Las secuencias de escape pueden ser cualquiera de las siguientes:  
  
|Valor|Secuencia de escape|Valor|Secuencia de escape|  
|-----------|-------------------------|-----------|-------------------------|  
|Nueva línea|\\n|Barra diagonal inversa|\\\\|  
|Tabulación horizontal|\\t|interrogación|? o \\?|  
|Tabulación vertical|\\v|Comilla simple|\\'|  
|Retroceso|\\b|Comilla doble|\\"|  
|Retorno de carro|\\r|Carácter nulo|\\0|  
|Avance de página|\\f|Octal|\\ooo|  
|Alerta \(campana\)|\\a|Hexadecimal|\\xhhh|  
  
 En el código siguiente se muestran algunos ejemplos de caracteres de escape que usan literales de cadena estrechos. La misma sintaxis es válida para los demás tipos literales de cadena.  
  
```cpp  
#include <iostream> using namespace std; int main() { char newline = '\n'; char tab = '\t'; char backspace = '\b'; char backslash = '\\'; char nullChar = '\0'; cout << "Newline character: " << newline << "ending" << endl; // Newline character: //  ending cout << "Tab character: " << tab << "ending" << endl; // Tab character : ending cout << "Backspace character: " << backspace << "ending" << endl; // Backspace character : ending cout << "Backslash character: " << backslash << "ending" << endl; // Backslash character : \ending cout << "Null character: " << nullChar << "ending" << endl; //Null character:  ending }  
```  
  
 **Específicos de Microsoft**  
  
 Para crear un valor a partir de un literal de carácter sin prefijo, el compilador convierte el carácter o la secuencia de caracteres entre comillas simples en valores de ocho bits dentro de un entero de 32 bits. Varios caracteres del literal rellenan los bytes correspondientes según sea necesario de orden superior a orden inferior. Para crear un valor `char`, el compilador usa el byte de orden inferior. Para crear un valor `wchar_t` o  `char16_t`, el compilador usa la palabra de orden inferior. El compilador advierte que el resultado se trunca si cualquiera de los bits se establece por encima del byte o la palabra asignados.  
  
```cpp  
char c0    = 'abcd';    // C4305, C4309, truncates to 'd' wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'  
```  
  
 Una secuencia de escape octal es una barra diagonal inversa seguida de una secuencia de hasta 3 dígitos octales. El comportamiento de una secuencia de escape octal que parece contener más de tres dígitos se trata como una secuencia octal de tres dígitos seguida de los dígitos posteriores como caracteres. Esto puede generar resultados sorprendentes. Por ejemplo:  
  
```cpp  
char c1 = '\100';   // '@' char c2 = '\1000';  // C4305, C4309, truncates to '0'   
```  
  
 Las secuencias de escape que parecen contener caracteres que no son octales se evalúan como una secuencia octal hasta el último carácter octal, seguido del resto de los caracteres. Por ejemplo:  
  
```cpp  
char c3 = '\009';   // '9' char c4 = '\089';   // C4305, C4309, truncates to '9' char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'  
```  
  
 Una secuencia de escape hexadecimal es una barra diagonal inversa seguida del carácter `x` y seguida de una secuencia de dígitos hexadecimales. Una secuencia de escape que no contiene ningún dígito hexadecimal produce el error del compilador C2153: “los literales hexadecimales deben tener al menos un dígito hexadecimal”. Los ceros a la izquierda se ignoran. Una secuencia de escape que parece tener caracteres hexadecimales y no hexadecimales se evalúa como una secuencia de escape hexadecimal hasta el último carácter hexadecimal, seguido de los caracteres no hexadecimales.   En un literal de carácter estrecho sin prefijo o con prefijo u8, el valor hexadecimal máximo es 0xFF. En un literal de carácter ancho con prefijo L o prefijo u, el valor hexadecimal máximo es 0xFFFF. En un literal de carácter ancho con prefijo U, el valor hexadecimal máximo es 0xFFFFFFFF.  
  
```cpp  
char c6 = '\x0050'; // 'P' char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'  
```  
  
 Si un literal de carácter ancho con prefijo `L` tiene más de un carácter, el valor se toma del primer carácter. Los caracteres subsiguientes se ignoran, a diferencia del comportamiento que se observa en el literal de carácter estrecho sin prefijo equivalente.  
  
```cpp  
wchar_t w1 = L'\100';   // L'@' wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored wchar_t w6 = L'\x0050'; // L'P' wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored  
```  
  
 **FIN de Específicos de Microsoft**  
  
 El carácter de barra diagonal inversa \(\\\) es un carácter de continuación de línea cuando se coloca al final de una línea. Si quiere que un carácter de barra diagonal inversa aparezca como un literal de carácter, debe escribir dos barras diagonales inversas en una fila \(`\\`\). Para obtener más información sobre el carácter de continuación de línea, consulte [Fases de traducción](../preprocessor/phases-of-translation.md).  
  
###  <a name="bkmk_UCN"></a> Nombres de carácter universal  
 En los literales de carácter y los literales de cadena nativa \(con formato\), se puede representar cualquier carácter mediante un nombre de carácter universal.  Los nombres de carácter universal se forman con un prefijo \\U seguido de un punto de código Unicode de ocho dígitos o con un prefijo \\u seguido de un punto de código Unicode de cuatro dígitos La totalidad de los dígitos \(ocho o cuatro, respectivamente\) debe estar presente para formar un nombre de carácter universal correctamente.  
  
```cpp  
char u1 = 'A';          // 'A' char u2 = '\101';       // octal, 'A' char u3 = '\x41';       // hexadecimal, 'A' char u4 = '\u0041';     // \u UCN 'A' char u5 = '\U00000041'; // \U UCN 'A'  
```  
  
 **Pares suplentes**  
  
 Los nombres de carácter universal no pueden codificar valores que se encuentran en el rango de punto de código suplente de D800 a DFFF. En el caso de pares suplentes Unicode, especifique el nombre de carácter universal mediante `\UNNNNNNNN`, donde NNNNNNNN es el punto de código de ocho dígitos para el carácter. El compilador genera un par suplente si es necesario.  
  
 En C\+\+03, el lenguaje solo permitía representar un subjuego de caracteres mediante sus propios nombres de carácter universal. También permitía algunos nombres de carácter universal que, en efecto, no representaban ningún carácter Unicode válido. Esto se corrigió en el estándar de C\+\+11. En C\+\+11, tanto los literales de carácter y cadena como los identificadores pueden usar nombres de carácter universal.  Para obtener más información sobre los nombres de carácter universal, consulte [Juegos de caracteres](../cpp/character-sets2.md). Para obtener más información sobre Unicode, consulte [Unicode](http://msdn.microsoft.com/library/dd374081\(v=vs.85\).aspx). Para obtener más información sobre los pares suplentes, consulte [Pares suplentes y caracteres complementarios](http://msdn.microsoft.com/library/dd374069\(v=vs.85\).aspx).  
  
## Literales de cadena  
 Un literal de cadena representa una secuencia de caracteres que, en conjunto, forman una cadena terminada en null. Los caracteres deben escribirse entre comillas. Hay los siguientes tipos de literales de cadena:  
  
### Literales de cadena estrechos  
 Un literal de cadena estrecho es una matriz sin prefijo, delimitada por comillas dobles y terminada en null del tipo `const` `char`\[`n`\], donde n es la longitud de la matriz en bytes. Un literal de cadena estrecho puede contener cualquier carácter gráfico, excepto las comillas dobles \(`"`\), la barra diagonal inversa \(`\`\) o el carácter de nueva línea \(\\n\). Un literal de cadena estrecho también puede contener las secuencias de escape antes mencionadas, así como nombres de carácter universal que caben en un byte.  
  
```cpp  
const char *narrow = "abcd"; // represents the string: yes\no const char *escaped = "yes\\no";  
```  
  
 **Cadenas con codificación UTF\-8**  
  
 Una cadena con codificación UTF\-8 es una matriz con prefijo u8, delimitada por comillas dobles y terminada en null del tipo `const` `char`\[`n`\], donde n es la longitud de la matriz codificada en bytes. Un literal de cadena con prefijo u8 puede tener cualquier carácter gráfico, excepto las comillas dobles \(`"`\), la barra diagonal inversa \(`\`\) o el carácter de nueva línea \(\\n\). También puede contener las secuencias de escape de secuencias antes mencionadas y cualquier nombre de carácter universal.  
  
```cpp  
const char* str1 = u8"Hello World"; const char* str2 = u8"\U0001F607 is O:-)";  
```  
  
### Literales de cadena anchos  
 Un literal de cadena ancho es una matriz terminada en null de valores `wchar_t` constantes que lleva el prefijo '`L`' y que contiene cualquier carácter gráfico excepto las comillas dobles \("\), la barra diagonal inversa \(\\\) o el carácter de nueva línea. También puede contener las secuencias de escape de secuencias antes mencionadas y cualquier nombre de carácter universal.  
  
```cpp  
const wchar_t* wide = L"zyxw"; const wchar_t* newline = L"hello\ngoodbye";  
```  
  
 **char16\_t y char32\_t \(C\+\+11\)**  
  
 C \+\+ 11 incluye los tipos de caracteres portables `char16_t` \(Unicode de 16 bits\) y `char32_t` \(32 bits Unicode\):  
  
```cpp  
auto s3 = u"hello"; // const char16_t* auto s4 = U"hello"; // const char32_t*  
```  
  
### Literales de cadena sin formato \(C\+\+11\)  
 Un literal de cadena sin formato es una matriz terminada en null \(de cualquier tipo de carácter\) que contiene cualquier carácter gráfico, incluidas las comillas dobles \("\), la barra diagonal inversa \(\\\) o el carácter de nueva línea. Los literales de cadena sin formato suelen usarse en expresiones regulares que utilizan clases de caracteres, y en las cadenas HTML y XML. Para obtener ejemplos, vea el siguiente artículo: [preguntas más frecuentes de Bjarne Stroustrup sobre C\+\+11](http://go.microsoft.com/fwlink/?LinkId=401172).  
  
```cpp  
// represents the string: An unescaped \ character const char* raw_narrow = R"(An unescaped \ character)"; const wchar_t* raw_wide = LR"(An unescaped \ character)"; const char*       raw_utf8  = u8R"(An unescaped \ character)"; const char16_t* raw_utf16 = uR"(An unescaped \ character)"; const char32_t* raw_utf32 = UR"(An unescaped \ character)";  
```  
  
 Un delimitador es una secuencia definida por el usuario de hasta 16 caracteres que precede inmediatamente al paréntesis de apertura de un literal de cadena sin formato, y sigue inmediatamente a su paréntesis de cierre.  Por ejemplo, en `R"abc(Hello"\()abc"` la secuencia de delimitador es `abc` y el contenido de la cadena es `Hello"\(`. Puede usar un delimitador para eliminar la ambigüedad de las cadenas sin formato que contienen comillas dobles y paréntesis. Esta llamada provoca un error del compilador:  
  
```cpp  
// meant to represent the string: )” const char* bad_parens = R"()")";  // error C2059  
```  
  
 Pero un delimitador lo resuelve:  
  
```cpp  
const char* good_parens = R"xyz()")xyz";  
```  
  
 Puede construir un literal de cadena sin formato en el que haya una línea nueva \(no el carácter de escape\) en el código fuente:  
  
```cpp  
// represents the string: hello //goodbye const wchar_t* newline = LR"(hello goodbye)";  
```  
  
### Literales std::string \(C\+\+14\)  
 Los literales std::string son implementaciones de la biblioteca estándar de literales definidos por el usuario \(véase abajo\) que se representan como "xyx"s \(con un sufijo `s`\). Este tipo de literal de cadena produce un objeto temporal de tipo std::string, std::wstring, std::u32string o std::u16string según el prefijo que se especifique. Cuando no se usa ningún prefijo, como en el caso de arriba, se genera un std::string. L"xyz"s produce un std::wstring. u"xyz"s produce un [std::u16string](../Topic/u16string.md) y U"xyz"s produce un [std::u32string](../Topic/u32string.md).  
  
```cpp  
//#include <string> //using namespace std::string_literals; string str{ "hello"s }; string str2{ u8"Hello World" }; wstring str3{ L"hello"s }; u16string str4{ u"hello"s }; u32string str5{ U"hello"s };  
```  
  
 El sufijo s también puede usarse en literales de cadena sin formato:  
  
```cpp  
u32string str6{ UR"(She said "hello.")"s };  
```  
  
 Los literales std::string se definen en el espacio de nombres `std::literals::string_literals` del archivo de encabezado \<string\>. Dado que tanto `std::literals::string_literals` como `std::literals` se declaran como [espacios de nombres alineados](../cpp/namespaces-cpp.md), `std::literals::string_literals` se trata automáticamente como si perteneciera directamente al espacio de nombres `std`.  
  
### Tamaño de literales de cadena  
 En cadenas char\* de ANSI y otras codificaciones de byte único \(no UTF\-8\), el tamaño \(en bytes\) de un literal de cadena es el número de caracteres más uno \(para el carácter nulo de terminación\). En el resto de los tipos de cadena, el tamaño no está estrictamente relacionado con el número de caracteres. UTF\-8 usa hasta cuatro elementos char para codificar algunas *unidades de código*; char16\_t o wchar\_t codificados como UTF\-16 pueden usar dos elementos \(para un total de cuatro bytes\) para codificar una única *unidad de código*.   En este ejemplo se muestra el tamaño, en bytes, de un literal de cadena ancho:  
  
```cpp  
const wchar_t* str = L"Hello!"; const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);  
```  
  
 Observe que `strlen()` y `wcslen()` no incluyen el tamaño del carácter nulo de terminación, cuyo tamaño es igual que el tamaño del elemento del tipo string: un byte en una cadena de char\*, dos bytes en cadenas wchar\_t\* o char16\_t\* y cuatro bytes en cadenas de char32\_t\*.  
  
 La longitud máxima de un literal de cadena es de 65535 bytes. Este límite se aplica a los literales de cadena estrechos y anchos.  
  
### Modificación de literales de cadena  
 Dado que los literales de cadena son constantes \(a excepción de los literales std:string\), intentar modificarlos \(por ejemplo, str\[2\] \= 'A'\) provoca un error del compilador.  
  
 **Específicos de Microsoft**  
  
 En Visual C\+\+, puede utilizar un literal de cadena para inicializar un puntero a `char` o a `wchar_t` no constantes. Esto se permite en el código C99, pero está en desuso en C\+\+98 y se eliminó en C\+\+11. Un intento de modificar la cadena produce una infracción de acceso, como en este ejemplo:  
  
```cpp  
wchar_t* str = L"hello"; str[2] = L'a'; // run-time error: access violation  
```  
  
 Puede hacer que el compilador emita un error cuando un literal de cadena se convierte en un puntero de carácter non\_const al establecer la opción del compilador [\/Zc:strictStrings \(Deshabilitar conversión de tipo de literal de cadena\)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md). Es recomendable para el código portable que cumple los estándares. También es conveniente usar la palabra clave `auto` para declarar punteros inicializados de literales de cadena, porque resuelve el tipo \(const\) correcto. Por ejemplo, en este ejemplo de código se detecta un intento de escribir en un literal de cadena en tiempo de compilación:  
  
```cpp  
auto str = L"hello"; str[2] = L'a'; // C3892: you cannot assign to a variable that is const.  
```  
  
 En algunos casos, pueden agruparse literales de cadena idénticos para ahorrar espacio en el archivo ejecutable. En la agrupación de literales de cadena, el compilador hace que todas las referencias a un literal de cadena determinado apunten a la misma ubicación de la memoria, en lugar de apuntar cada una a una instancia distinta del literal de cadena. Para habilitar la agrupación de cadenas, use la opción del compilador [\/GF](../build/reference/gf-eliminate-duplicate-strings.md).  
  
 **Fin de Específicos de Microsoft**  
  
### Concatenación de literales de cadena adyacentes  
 Los literales de cadena anchos o estrechos adyacentes se concatenan. Esta declaración:  
  
```cpp  
char str[] = "12" "34";  
```  
  
 es idéntica a esta declaración:  
  
```cpp  
char atr[] = "1234";  
```  
  
 y a esta declaración:  
  
```cpp  
char atr[] =  "12\ 34";  
```  
  
 El uso de códigos de escape hexadecimales insertados para especificar literales de cadena puede producir resultados inesperados. El ejemplo siguiente está pensado para crear un literal de cadena que contiene el carácter ASCII 5, seguido de los caracteres f, i, v y e:  
  
```cpp  
"\x05five"  
```  
  
 El resultado real es 5F hexadecimal, que es el código ASCII de un carácter de subrayado, seguido de los caracteres i, v y e. En obtener el resultado correcto, puede usar una de las siguientes declaraciones:  
  
```cpp  
"\005five"     // Use octal literal. "\x05" "five"  // Use string splicing.  
```  
  
 Los literales std::string, al ser tipos std::string, pueden concatenarse con el operador \+ que se define para tipos [basic\_string](../standard-library/basic-string-class.md). También pueden concatenarse de la misma manera que literales de cadena adyacentes. En ambos casos, la codificación de cadena y el sufijo deben coincidir:  
  
```cpp  
auto x1 = "hello" " " " world"; // OK auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes  
```  
  
### Literales de cadena con nombres de caracteres universales  
 Los literales de cadena nativos \(con formato\) pueden usar nombres de carácter universal para representar cualquier carácter, siempre que el nombre de carácter universal pueda codificarse como uno o varios caracteres en el tipo de cadena.  Por ejemplo, no se puede codificar un nombre de carácter universal que representa un carácter extendido en una cadena de caracteres estrechos mediante la página de códigos ANSI, pero puede codificarse en cadenas de caracteres estrechos de algunas páginas de códigos multibyte, así como en cadenas UTF\-8 o en una cadena de caracteres anchos. En C\+\+11, la compatibilidad con Unicode se extiende mediante los tipos de cadena char16\_t\* y char32\_t\*:  
  
```cpp  
// ASCII smiling face const char*     s1 = ":-)"; // UTF-16 (on Windows) encoded WINKING FACE (U+1F609) const wchar_t*  s2 = L"😉 = \U0001F609 is ;-)"; // UTF-8  encoded SMILING FACE WITH HALO (U+1F607) const char*     s3 = u8"😇 = \U0001F607 is O:-)"; // UTF-16 encoded SMILING FACE WITH OPEN MOUTH (U+1F603) const char16_t* s4 = u"😃 = \U0001F603 is :-D"; // UTF-32 encoded SMILING FACE WITH SUNGLASSES (U+1F60E) const char32_t* s5 = U"😎 = \U0001F60E is B-)";  
```  
  
## Vea también  
 [Juegos de caracteres](../cpp/character-sets2.md)   
 [Literales numéricos, booleanos y de puntero](../cpp/numeric-boolean-and-pointer-literals-cpp.md)   
 [Literales definidos por el usuario](../cpp/user-defined-literals-cpp.md)