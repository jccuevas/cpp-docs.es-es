---
title: '##define (directiva) (C/C ++)'
ms.date: 11/04/2016
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: dec555de64a3ebd166bdff5558957f09e1c2755e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653757"
---
# <a name="define-directive-cc"></a>#define (Directiva) (C/C++)

El **#define** crea un *macro*, que es la asociación de un identificador o identificador parametrizado con una cadena de token. Una vez definida la macro, el compilador puede sustituir la cadena de token para cada aparición del identificador del archivo de código fuente.

## <a name="syntax"></a>Sintaxis

`#define` *identificador* *token-string*<sub>participar</sub>

`#define` *identificador* `(` *identificador*<sub>opt</sub> `,` *...*  `,` *identificador*<sub>opt</sub> `)` *token-string*<sub>participar</sub>

## <a name="remarks"></a>Comentarios

El **#define** directiva hace que el compilador sustituya *token-string* cada aparición de *identificador* en el archivo de origen. El *identificador* se sustituye solo cuando forma un token. Es decir, *identificador* no se reemplaza si aparece en un comentario, en una cadena o como parte de un identificador más largo. Para obtener más información, consulte [Tokens](../cpp/tokens-cpp.md).

El *token-string* argumento consta de una serie de tokens, como palabras clave, constantes o instrucciones completas. Uno o más caracteres de espacio en blanco deben separar *token-string* desde *identificador*. Este espacio en blanco no se considera parte de texto sustituido, ni tampoco cualquier espacio en blanco que vaya después del último token del texto.

Un `#define` sin un *token-string* quita las apariciones de *identificador* desde el archivo de origen. El *identificador* permanece definido y se pueden probar mediante el uso de la `#if defined` y `#ifdef` directivas.

El segundo formato de sintaxis define una macro de tipo función con parámetros. Este formato acepta una lista opcional de parámetros que deben aparecer entre paréntesis. Una vez definido, cada repetición posterior de la macro *identificador*( *identificador*<sub>opt</sub>,..., *identificador* <sub>opt</sub> ) se reemplaza con una versión de la *token-string* argumento que tiene argumentos reales reemplazados por parámetros formales.

Nombres de parámetros formales aparecen en *token-string* para marcar las ubicaciones donde se sustituyen los valores reales. Cada nombre de parámetro puede aparecer varias veces en *token-string*, y los nombres pueden aparecer en cualquier orden. El número de argumentos de la llamada debe coincidir con el número de parámetros en la definición de macro. El uso racional de paréntesis garantiza que los argumentos complejos se interpreten correctamente.

Los parámetros formales de la lista están separados por comas. Cada nombre de la lista debe ser único, y la lista se debe incluir entre paréntesis. No pueden separar espacios en blanco *identificador* y el paréntesis de apertura. Utilice la concatenación de línea, coloque una barra diagonal inversa (`\`) inmediatamente antes del carácter de nueva línea, para las directivas largas en líneas de código fuente. El ámbito de un nombre de parámetro formal se extiende a la nueva línea que finaliza *token-string*.

Cuando una macro se ha definido con el segundo formato de sintaxis, las instancias textuales subsiguientes seguidas de una lista de argumentos indican una llamada a macro. Los argumentos reales que siguen a una instancia de *identificador* en el archivo de código fuente coincidan con los parámetros formales correspondientes en la definición de macro. Cada parámetro formal en *token-string* que no esté precedido por una conversión a cadenas (`#`), charizing (`#@`), o pegado de token (`##`) (operador), o no seguido de un `##` operador, es Reemplazar por el argumento real correspondiente. Cualquier macro en el argumento real se expande antes de que la directiva reemplace el parámetro formal. (Se describen los operadores en [operadores de preprocesador](../preprocessor/preprocessor-operators.md).)

Los siguientes ejemplos de macros con argumentos muestran el segundo formato de la **#define** sintaxis:

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

Los argumentos con efectos secundarios a veces hacen que las macros den resultados inesperados. Un parámetro formal determinado puede aparecer más de una vez en *token-string*. Si ese parámetro formal se sustituye por una expresión con efectos secundarios, la expresión, con sus efectos secundarios, se puede evaluar más de una vez. (Vea los ejemplos en [operador de pegado de Token (##)](../preprocessor/token-pasting-operator-hash-hash.md).)

La directiva `#undef` hace que se olvide la definición de preprocesador de un identificador. Consulte [la directiva #undef](../preprocessor/hash-undef-directive-c-cpp.md) para obtener más información.

Si se produce el nombre de la macro que se define en *token-string* (incluso como resultado de otra expansión de macro), no se expande.

Un segundo **#define** para una macro con el mismo nombre genera una advertencia a menos que la segunda secuencia de token es idéntica al primero.

**Específicos de Microsoft**

Microsoft C/C++ permite volver a definir una macro si la nueva definición es sintácticamente idéntica a la definición original. Es decir, las dos definiciones pueden tener distintos nombres de parámetro. Este comportamiento difiere de ANSI C, que requiere que las dos definiciones sean léxicamente idénticas.

Por ejemplo, las dos macros siguientes son idénticas salvo en los nombres de parámetro. ANSI C no permite esa nueva definición, pero Microsoft C o C++ lo compila sin errores.

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

En este ejemplo se ilustra la **#define** directiva:

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

Definición de macros y constantes con el [/D](../build/reference/d-preprocessor-definitions.md) opción del compilador tiene el mismo efecto que usar un **#define** preprocesamiento de directiva al principio del archivo. Se pueden definir hasta 30 macros mediante la opción /D.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)