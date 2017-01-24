---
title: "#define (Directiva) (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#define"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#define (directiva)"
  - "#define (directiva), sintaxis"
  - "define (directiva) (#define)"
  - "define (directiva) (#define), sintaxis"
  - "preprocesador, directivas"
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #define (Directiva) (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`#define` crea una *macro*, que es la asociación de un identificador o identificador parametrizado con una cadena de token.  Una vez definida la macro, el compilador puede sustituir la cadena de token para cada aparición del identificador del archivo de código fuente.  
  
## Sintaxis  
 `#define` *identifier* *token\-string*opc  
  
 `#define` *identifier*`(` *identifier*opc`,` *...* `,` *identifier*opc `)` *token\-string*opc  
  
## Comentarios  
 La directiva `#define` hace que el compilador sustituya *token\-string* para cada aparición de *identifier* en el archivo de código fuente.  *identifier* se sustituye solo cuando forma un token.  Es decir, *identifier* no se reemplaza si aparece en un comentario o cadena, o como parte de un identificador más largo.  Para obtener más información, vea [Tokens de C\+\+](../cpp/tokens-cpp.md).  
  
 El argumento *token\-string* consta de una serie de tokens, como palabras clave, constantes o instrucciones completas.  Uno o más caracteres de espacio en blanco deben separar *token\-string* de *identifier*.  Este espacio en blanco no se considera parte de texto sustituido, ni tampoco cualquier espacio en blanco que vaya después del último token del texto.  
  
 `#define` sin *token\-string* quita las apariciones de *identifier* del archivo de código fuente.  *identifier* permanece definido y se puede probar mediante las directivas `#if defined` e `#ifdef`.  
  
 El segundo formato de sintaxis define una macro de tipo función con parámetros.  Este formato acepta una lista opcional de parámetros que deben aparecer entre paréntesis.  Una vez definida la macro, cada repetición posterior de *identifier*\( *identifier*opt, …, *identifier*opt \) se reemplaza con una versión del argumento *token\-string* que tiene los argumentos reales en lugar de parámetros formales.  
  
 Los nombres de los parámetros formales aparecen en *token\-string* para marcar las ubicaciones donde se sustituyen los valores reales.  Cada nombre de parámetro puede aparecer varias veces en *token\-string*, mientras que los nombres pueden aparecer en cualquier orden.  El número de argumentos de la llamada debe coincidir con el número de parámetros en la definición de macro.  El uso racional de paréntesis garantiza que los argumentos complejos se interpreten correctamente.  
  
 Los parámetros formales de la lista están separados por comas.  Cada nombre de la lista debe ser único, y la lista se debe incluir entre paréntesis.  No puede haber espacios que separen *identifier* y el paréntesis de apertura.  Utilice la concatenación de línea \(coloque una barra diagonal inversa \(`\`\) inmediatamente antes del carácter de nueva línea\) para las directivas largas que ocupen varias líneas de código fuente.  El ámbito de un nombre de parámetro formal se extiende a la nueva línea que finaliza *token\-string*.  
  
 Cuando una macro se ha definido con el segundo formato de sintaxis, las instancias textuales subsiguientes seguidas de una lista de argumentos indican una llamada a macro.  Los argumentos reales que siguen a una instancia de *identifier* en el archivo de código fuente coinciden con los parámetros formales correspondientes en la definición de macro.  Cada parámetro formal de *token\-string* que no va precedido de un operador de generación de cadenas \(`#`\), charizing \(`#@`\) o de pegado de token \(`##`\), ni va seguido de un operador `##`, se reemplaza con el argumento real correspondiente.  Cualquier macro en el argumento real se expande antes de que la directiva reemplace el parámetro formal. \(Los operadores se describen en [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)\).  
  
 Los siguientes ejemplos de macros con argumentos muestran el segundo formato de sintaxis de `#define`:  
  
```  
// Macro to define cursor lines   
#define CURSOR(top, bottom) (((top) << 8) | (bottom))  
  
// Macro to get a random integer with a specified range   
#define getrandom(min, max) \  
    ((rand()%(int)(((max) + 1)-(min)))+ (min))  
```  
  
 Los argumentos con efectos secundarios a veces hacen que las macros den resultados inesperados.  Un parámetro formal determinado puede aparecer más de una vez en *token\-string*.  Si ese parámetro formal se sustituye por una expresión con efectos secundarios, la expresión, con sus efectos secundarios, se puede evaluar más de una vez. \(Vea los ejemplos en [Operador de pegado de token \(\#\#\)](../preprocessor/token-pasting-operator-hash-hash.md)\).  
  
 La directiva `#undef` hace que se olvide la definición de preprocesador de un identificador.  Vea el tema sobre la [directiva \#undef](../preprocessor/hash-undef-directive-c-cpp.md) para obtener más información.  
  
 Si el nombre de la macro que se define aparece en *token\-string* \(incluso como resultado de otra expansión de macro\), no se expande.  
  
 Una segunda directiva `#define` para una macro con el mismo nombre genera una advertencia, a menos que la segunda secuencia de token sea idéntica a la primera.  
  
 **Específicos de Microsoft**  
  
 Microsoft C\/C\+\+ permite volver a definir una macro si la nueva definición es sintácticamente idéntica a la definición original.  Es decir, las dos definiciones pueden tener distintos nombres de parámetro.  Este comportamiento difiere de [!INCLUDE[vcpransi](../preprocessor/includes/vcpransi_md.md)] C, que requiere que las dos definiciones sean léxicamente idénticas.  
  
 Por ejemplo, las dos macros siguientes son idénticas salvo en los nombres de parámetro.  [!INCLUDE[vcpransi](../preprocessor/includes/vcpransi_md.md)] C no permite esa nueva definición, pero Microsoft C\/C\+\+ realiza la compilación sin errores.  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( a1 * a2 )  
```  
  
 Por otra parte, las dos macros siguientes no son idénticas y se generará una advertencia en Microsoft C\/C\+\+.  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( b1 * b2 )  
```  
  
 **FIN de Específicos de Microsoft**  
  
 En este ejemplo se muestra la directiva `#define`:  
  
```  
#define WIDTH       80  
#define LENGTH      ( WIDTH + 10 )  
```  
  
 La primera instrucción define el identificador `WIDTH` como la constante de tipo entero 80 y define `LENGTH` en términos de `WIDTH` y la constante de tipo entero 10.  Cada aparición de `LENGTH` se reemplaza con \(`WIDTH + 10`\).  A su vez, cada aparición de `WIDTH + 10` se reemplaza con la expresión \(`80 + 10`\).  Los paréntesis alrededor de `WIDTH + 10` son importantes, porque controlan la interpretación en instrucciones como las siguientes:  
  
```  
var = LENGTH * 20;  
```  
  
 Después de la fase de preprocesamiento, la instrucción se convierte en:  
  
```  
var = ( 80 + 10 ) * 20;  
```  
  
 que se evalúa como 1800.  Sin paréntesis, el resultado es:  
  
```  
var = 80 + 10 * 20;  
```  
  
 que se evalúa como 280.  
  
 **Específicos de Microsoft**  
  
 La definición de macros y constantes con la opción [\/D](../build/reference/d-preprocessor-definitions.md) del compilador tiene el mismo efecto que el uso de una directiva de procesamiento `#define` al principio del archivo.  Se pueden definir hasta 30 macros mediante la opción \/D.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)