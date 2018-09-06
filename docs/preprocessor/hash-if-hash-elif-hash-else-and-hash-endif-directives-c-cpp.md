---
title: '#if, #elif, #else y #endif (directivas) (C ++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
dev_langs:
- C++
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dcacaab21ca763a9ce45a9ab6eb503cd6fc7b74
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753846"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if, #elif, #else, and #endif (Directivas) (C/C++)

El **#if** la directiva con la **#elif**, **#else**, y **#endif** directivas, controla la compilación de partes de un archivo de origen. Si la expresión que se escribe (después de la **#if**) tiene un valor distinto de cero, el grupo de líneas inmediatamente después de la **#if** directiva se guarda en la unidad de traducción.

## <a name="grammar"></a>Gramática

*condicional* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-partes de la parte de si*<sub>opt</sub> *parte else*<sub>opt</sub> *endif-línea*

*parte de si* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*texto de la línea de If*

*If-línea* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if***expresión constante* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef***identificador* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef***identificador* 

*elif-partes* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*texto elif-línea*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*texto de elif-partes elif-línea*

*elif-línea* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif***expresión constante* 

*otro-parte* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*texto de la línea Else*

*otro-línea* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*endif-línea* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

Cada **#if** directiva en un archivo de origen debe coincidir por un cierre **#endif** directiva. Cualquier número de **#elif** directivas pueden aparecer entre el **#if** y **#endif** directivas, pero a lo sumo una **#else** se permite la directiva. El **#else** directiva, si está presente, debe ser la última directiva antes de **#endif**.

El **#if**, **#elif**, **#else**, y **#endif** directivas pueden anidarse en partes de texto de otros **#if**directivas. Cada uno anidado **#else**, **#elif**, o **#endif** directiva pertenece a la anterior más cercana **#if** directiva.

Todas las directivas de compilación condicional, como **#if** y **#ifdef**, debe coincidir con el cierre **#endif** directivas antes del final del archivo; en caso contrario, un error se genera el mensaje. Cuando las directivas de compilación condicional están contenidas en archivos de inclusión, deben cumplir las mismas condiciones: no debe haber directivas de compilación condicional sin coincidencia al final del archivo de inclusión.

Reemplazo de macros se realiza dentro de la parte de la línea de comandos que sigue un **#elif** de comandos, por lo que se puede usar una llamada de macro en el *expresión-constante*.

El preprocesador selecciona una de las apariciones dadas de *texto* para su posterior procesamiento. Un bloque especificado en *texto* puede ser cualquier secuencia de texto. Puede ocupar más de una línea. Normalmente *texto* es texto del programa que tiene un significado para el compilador o el preprocesador.

El preprocesador procesa seleccionado *texto* y lo pasa al compilador. Si *texto* contiene las directivas de preprocesador, el preprocesador ejecuta esas directivas. Solo se compilan los bloques de texto seleccionados por el preprocesador.

El preprocesador selecciona una única *texto* al evaluar la expresión constante que sigue a cada elemento de **#if** o **#elif** directiva hasta que encuentra una constante true (distinto de cero) expresión. Selecciona todo el texto (incluido a partir de otras directivas de preprocesador **#**) hasta su asociado **#elif**, **#else**, o **#endif** .

Si todas las apariciones de *expresión-constante* son false, o si no hay ningún **#elif** aparecen las directivas, el preprocesador selecciona el bloque de texto después de la **#else** cláusula. Si el **#else** cláusula se omite y todas las instancias de *expresión-constante* en el **#if** bloque son false, no se selecciona ningún bloque de texto.

El *expresión-constante* expresión constante entera con estas restricciones adicionales:

- Las expresiones deben tener un tipo entero y puede incluir solo constantes de tipo entero, constantes de caracteres y el **definido** operador.

- La expresión no puede utilizar `sizeof` o un operador de conversión de tipo.

- Es posible que el entorno de destino no pueda representar todos los intervalos de enteros.

- La traducción representa el tipo **int** igual tipo **largo**, y **int sin signo** igual **unsigned long**.

- El traductor puede traducir constantes de caracteres a un conjunto de valores de código diferentes del conjunto para el entorno de destino. Para determinar las propiedades del entorno de destino, compruebe los valores de las macros de LIMITS.H en una aplicación compilada para el entorno de destino.

- La expresión no debe realizar ninguna consulta de ambiente y debe permanecer aislada de los detalles de implementación del equipo de destino.

## <a name="defined"></a>definición

El operador de preprocesador **definido** se puede usar en expresiones constantes especiales, como se muestra en la siguiente sintaxis:

defined( `identifier` )

defined `identifier`

Esta expresión constante se considera true (distinto de cero) si el *identificador* está definido actualmente; en caso contrario, la condición es false (0). Un identificador definido como texto vacío se considera definido. El **definido** directiva puede utilizarse en una **#if** y un **#elif** directiva, pero ningún otro lugar.

En el ejemplo siguiente, la **#if** y **#endif** directivas controlan la compilación de una de las tres llamadas de función:

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

La llamada de función a `credit` se compila si el identificador `CREDIT` está definido. Si el identificador `DEBIT` está definido, se compila la llamada de función a `debit`. Si no está definido ninguno de los identificadores, se compila la llamada a `printerror`. Observe que `CREDIT` y `credit` son identificadores distintos en C y C++ por la distinción entre mayúsculas y minúsculas de ambos.

Las instrucciones de compilación condicional del ejemplo siguiente suponen una constante simbólica previamente definida denominada `DLEVEL`.

```C
#if DLEVEL > 5
    #define SIGNAL  1
    #if STACKUSE == 1
        #define STACK   200
    #else
        #define STACK   100
    #endif
#else
    #define SIGNAL  0
    #if STACKUSE == 1
        #define STACK   100
    #else
        #define STACK   50
    #endif
#endif
#if DLEVEL == 0
    #define STACK 0
#elif DLEVEL == 1
    #define STACK 100
#elif DLEVEL > 5
    display( debugptr );
#else
    #define STACK 200
#endif
```

La primera **#if** bloque muestra dos conjuntos de anidada **#if**, **#else**, y **#endif** directivas. El primer conjunto de directivas se procesa solo si `DLEVEL > 5` es true. En caso contrario, las instrucciones después **#else** se procesan.

El **#elif** y **#else** directivas en el segundo ejemplo se utilizan para realizar una de las cuatro opciones, según el valor de `DLEVEL`. La constante `STACK` se establece en 0, 100 o 200, según de la definición de `DLEVEL`. Si `DLEVEL` es mayor que 5, la instrucción

```C
#elif DLEVEL > 5
display(debugptr);
```

se compila y `STACK` no está definido.

Un uso común para la compilación condicional es evitar inclusiones múltiples del mismo archivo de encabezado. En C++, donde las clases suelen definirse en archivos de encabezado, se pueden utilizar construcciones como la siguiente para evitar varias definiciones:

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
...
};

#endif // !defined( EXAMPLE_H )
```

El código anterior realiza comprobaciones para ver si se define la constante simbólica `EXAMPLE_H`. Si es así el archivo se ha incluido y no necesita ya volver a procesarse. Si no, se define la constante `EXAMPLE_H` para marcar EXAMPLE.H como ya procesado.

## <a name="hasinclude"></a>__has_include

**Visual Studio 2017 versión 15.3 y versiones posterior**: determina si un encabezado de la biblioteca está disponible para su inclusión:

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```

## <a name="see-also"></a>Vea también

[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)