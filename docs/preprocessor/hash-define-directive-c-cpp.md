---
title: '#define (Directiva) (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: b72e2468b9e9984237c81f5cdb3c5691fe95cbd0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216279"
---
# <a name="define-directive-cc"></a>#define (Directiva) (C++C/)

El **#define** crea una *macro*, que es la Asociación de un identificador o un identificador parametrizado con una cadena de token. Una vez definida la macro, el compilador puede sustituir la cadena de token para cada aparición del identificador del archivo de código fuente.

## <a name="syntax"></a>Sintaxis

> **#define** *identificador* de *token-cadena* <sub>OPT</sub>\
> **#define** *identificador* de **(** *identificador*<sub>OPT</sub> **,** ... **,** *identificador* de <sub>OPT</sub> **)** *token: cadena*<sub>opcional</sub>

## <a name="remarks"></a>Comentarios

La directiva **#define** hace que el compilador sustituya por la *cadena de token* para cada aparición del *identificador* en el archivo de código fuente. El *identificador* solo se reemplaza cuando forma un token. Es decir, el *identificador* no se reemplaza si aparece en un comentario, en una cadena o como parte de un identificador más largo. Para obtener más información, consulte [tokens](../cpp/tokens-cpp.md).

El argumento *token-String* se compone de una serie de tokens, como palabras clave, constantes o instrucciones completas. Uno o más caracteres de espacio en blanco deben separar *la cadena de token* del *identificador*. Este espacio en blanco no se considera parte de texto sustituido, ni tampoco cualquier espacio en blanco que vaya después del último token del texto.

Un `#define` sin una *cadena de token* quita las apariciones del *identificador* del archivo de código fuente. El *identificador* permanece definido y se puede probar mediante las `#if defined` directivas y. `#ifdef`

El segundo formato de sintaxis define una macro de tipo función con parámetros. Este formato acepta una lista opcional de parámetros que deben aparecer entre paréntesis. Una vez definida la macro, cada repetición subsiguiente del *identificador*( *Identifier*<sub>OPT</sub>,..., *Identifier*<sub>OPT</sub> ) se reemplaza con una versión del argumento de cadena de *token* que tiene argumentos reales. se sustituye por los parámetros formales.

Los nombres de parámetros formales aparecen en *cadena de token* para marcar las ubicaciones donde se sustituyen los valores reales. Cada nombre de parámetro puede aparecer varias veces en la *cadena de token*y los nombres pueden aparecer en cualquier orden. El número de argumentos de la llamada debe coincidir con el número de parámetros en la definición de macro. El uso racional de paréntesis garantiza que los argumentos complejos se interpreten correctamente.

Los parámetros formales de la lista están separados por comas. Cada nombre de la lista debe ser único, y la lista se debe incluir entre paréntesis. Ningún espacio puede separar el *identificador* y el paréntesis de apertura. Usar la concatenación de línea: coloca una barra`\`diagonal inversa () inmediatamente antes del carácter de nueva línea, para las directivas largas en varias líneas de código fuente. El ámbito de un nombre de parámetro formal se extiende a la nueva línea que finaliza la *cadena de token*.

Cuando una macro se ha definido con el segundo formato de sintaxis, las instancias textuales subsiguientes seguidas de una lista de argumentos indican una llamada a macro. Los argumentos reales que siguen a una instancia de *Identifier* en el archivo de código fuente coinciden con los parámetros formales correspondientes en la definición de macro. Cada parámetro formal de *la cadena de token* que no va precedido de un operador de`#`generación de cadenas ()`#@`, carácter () o de pegado`##`de token (), o no seguido `##` de un operador, se reemplaza por el correspondiente argumento real. Cualquier macro en el argumento real se expande antes de que la directiva reemplace el parámetro formal. (Los operadores se describen en [operadores de preprocesador](../preprocessor/preprocessor-operators.md)).

Los siguientes ejemplos de macros con argumentos muestran el segundo formato de la sintaxis de **#define** :

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

Los argumentos con efectos secundarios a veces hacen que las macros den resultados inesperados. Un parámetro formal determinado puede aparecer más de una vez en *la cadena de token*. Si ese parámetro formal se sustituye por una expresión con efectos secundarios, la expresión, con sus efectos secundarios, se puede evaluar más de una vez. (Vea los ejemplos en [operador de pegado de tokens (# #)](../preprocessor/token-pasting-operator-hash-hash.md)).

La directiva `#undef` hace que se olvide la definición de preprocesador de un identificador. Vea [la directiva #undef](../preprocessor/hash-undef-directive-c-cpp.md) para obtener más información.

Si el nombre de la macro que se está definiendo se produce en la *cadena de token* (incluso como resultado de otra expansión de macro), no se expande.

Un segundo **#define** para una macro con el mismo nombre genera una advertencia a menos que la segunda secuencia del token sea idéntica a la primera.

**Específicos de Microsoft**

Microsoft C/C++ permite volver a definir una macro si la nueva definición es sintácticamente idéntica a la definición original. Es decir, las dos definiciones pueden tener distintos nombres de parámetro. Este comportamiento difiere de ANSI C, que requiere que las dos definiciones sean léxicamente idénticas.

Por ejemplo, las dos macros siguientes son idénticas salvo en los nombres de parámetro. ANSI C no permite esa nueva definición, pero Microsoft C/C++ lo compila sin errores.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

Por otra parte, las dos macros siguientes no son idénticas y se generará una advertencia en Microsoft C/C++.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**FIN de Específicos de Microsoft**

En este ejemplo se muestra la Directiva de **#define** :

```C
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```

La primera instrucción define el identificador `WIDTH` como la constante de tipo entero 80 y define `LENGTH` en términos de `WIDTH` y la constante de tipo entero 10. Cada aparición de `LENGTH` se reemplaza con (`WIDTH + 10`). A su vez, cada aparición de `WIDTH + 10` se reemplaza con la expresión (`80 + 10`). Los paréntesis alrededor de `WIDTH + 10` son importantes, porque controlan la interpretación en instrucciones como las siguientes:

```C
var = LENGTH * 20;
```

Después de la fase de preprocesamiento, la instrucción se convierte en:

```C
var = ( 80 + 10 ) * 20;
```

que se evalúa como 1800. Sin paréntesis, el resultado es:

```C
var = 80 + 10 * 20;
```

que se evalúa como 280.

**Específicos de Microsoft**

La definición de macros y constantes con la opción del compilador [/d](../build/reference/d-preprocessor-definitions.md) tiene el mismo efecto que el uso de una directiva de preprocesamiento **#define** al principio del archivo. Se pueden definir hasta 30 macros mediante la opción /D.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)
