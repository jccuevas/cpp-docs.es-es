---
title: '#if, #elif, #elsey #endif (Directivas) (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
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
ms.openlocfilehash: 2b7ed4733dcafda793b9a945c3f40739b52e040a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220343"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if, #elif, #else y directivas de #endif (C/C++)

La directiva **#if** , con las directivas **#elif**, **#else**y **#endif** , controla la compilación de partes de un archivo de código fuente. Si la expresión que escribe (después de la **#if**) tiene un valor distinto de cero, el grupo de líneas inmediatamente después de la directiva de **#if** se mantiene en la unidad de traducción.

## <a name="grammar"></a>Gramática

*condicional* : \
&nbsp;&nbsp;&nbsp;&nbsp;*If-Part Elif-* Parts <sub>OPT</sub> *parte de else* <sub>OPT</sub> *endif-línea*

*si-parte* : \
&nbsp;&nbsp;&nbsp;&nbsp;*texto if-line*

*If-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *expresión constante*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *identificador* de\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *identificador* de

*Elif-partes* : \
&nbsp;&nbsp;&nbsp;&nbsp;*texto de la línea Elif*\
&nbsp;&nbsp;&nbsp;&nbsp;*texto de la línea Elif-Parts*

*Elif-línea* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *expresión constante*

*else-Part* : \
&nbsp;&nbsp;&nbsp;&nbsp;*texto de la línea adicional*

*else-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-línea* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

## <a name="remarks"></a>Comentarios

Cada directiva de **#if** de un archivo de código fuente debe coincidir con una directiva de cierre **#endif** . Puede aparecer cualquier número de directivas de **#elif** entre las directivas **#if** y **#endif** , pero se permite como máximo una directiva **#else** . La directiva **#else** , si está presente, debe ser la última Directiva antes de **#endif**.

Las directivas **#if**, **#elif**, **#else**y **#endif** se pueden anidar en las partes de *texto* de otras directivas de **#if** . Cada directiva anidada **#else**, **#elif**o **#endif** pertenece a la Directiva de **#if** precedente más cercana.

Todas las directivas de compilación condicional, como **#if** y **#ifdef**, deben coincidir con una directiva de cierre **#endif** antes del final del archivo. De lo contrario, se genera un mensaje de error. Cuando las directivas de compilación condicional están contenidas en archivos de inclusión, deben cumplir las mismas condiciones: No debe haber ninguna directiva de compilación condicional sin coincidencia al final del archivo de inclusión.

El reemplazo de macros se realiza dentro de la parte de la línea que sigue a un comando de **#elif** , por lo que se puede usar una llamada de macro en *Constant-Expression*.

El preprocesador selecciona una de las apariciones de *texto* dadas para su posterior procesamiento. Un bloque especificado en *texto* puede ser cualquier secuencia de texto. Puede ocupar más de una línea. Normalmente, el *texto* es el texto de programa que tiene significado para el compilador o el preprocesador.

El preprocesador procesa el *texto* seleccionado y lo pasa al compilador. Si el *texto* contiene directivas de preprocesador, el preprocesador realiza esas directivas. Solo se compilan los bloques de texto seleccionados por el preprocesador.

El preprocesador selecciona un solo elemento de *texto* mediante la evaluación de la expresión constante que sigue a cada **#if** o **#elif** Directiva hasta que encuentra una expresión constante true (distinto de cero). Selecciona todo el texto (incluidas otras directivas de preprocesador que comienzan **#** por) hasta su **#elif**, **#else**o **#endif**asociados.

Si todas las apariciones de *Constant-Expression* son false o si no aparecen directivas de **#elif** , el preprocesador selecciona el bloque de texto después de la cláusula **#else** . Cuando no hay ninguna cláusula **#else** y todas las instancias de *Constant-Expression* en el bloque **#if** son false, no se selecciona ningún bloque de texto.

*Constant-Expression* es una expresión constante entera con estas restricciones adicionales:

- Las expresiones deben tener un tipo entero y solo pueden incluir constantes enteras, constantes de caracteres y el operador **definido** .

- La expresión no puede `sizeof` utilizar o un operador de conversión de tipos.

- Es posible que el entorno de destino no pueda representar todos los intervalos de enteros.

- La traducción representa el tipo **int** del mismo modo que el tipo **Long**y Unsigned **int** de la misma manera que unsigned **Long**.

- El traductor puede traducir constantes de caracteres a un conjunto de valores de código diferentes del conjunto para el entorno de destino. Para determinar las propiedades del entorno de destino, use una aplicación compilada para ese entorno para comprobar los valores de los *límites. H* macros.

- La expresión no debe consultar el entorno y debe permanecer aislada de los detalles de implementación en el equipo de destino.

## <a name="preprocessor-operators"></a>Operadores de preprocesador

### <a name="defined"></a>definido

El operador de preprocesador **definido** se puede usar en expresiones constantes especiales, como se muestra en la sintaxis siguiente:

> **definido (** *identificador* **)** \
> **definido** *identificador* de

Esta expresión constante se considera true (distinto de cero) si el *identificador* está definido actualmente. De lo contrario, la condición es false (0). Un identificador definido como texto vacío se considera definido. El operador **Defined** se puede usar en una **#if** y una directiva **#elif** , pero en ningún otro caso.

En el ejemplo siguiente, las directivas **#if** y **#endif** controlan la compilación de una de las tres llamadas de función:

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

La llamada de función a `credit` se compila si el identificador `CREDIT` está definido. Si el identificador `DEBIT` está definido, se compila la llamada de función a `debit`. Si no está definido ninguno de los identificadores, se compila la llamada a `printerror`. Y son identificadores distintos en C y C++ porque sus casos son diferentes. `credit` `CREDIT`

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

El primer bloque de **#if** muestra dos conjuntos de directivas anidadas de **#if**, **#else**y **#endif** . El primer conjunto de directivas se procesa solo si `DLEVEL > 5` es true. De lo contrario, se procesan las instrucciones después de **#else** .

Las directivas **#elif** y **#else** del segundo ejemplo se utilizan para tomar una de las cuatro opciones, según el valor de `DLEVEL`. La constante `STACK` se establece en 0, 100 o 200, según de la definición de `DLEVEL`. Si `DLEVEL` es mayor que 5, la instrucción

```C
#elif DLEVEL > 5
display(debugptr);
```

se compila y `STACK` no está definido.

Un uso común para la compilación condicional es evitar inclusiones múltiples del mismo archivo de encabezado. En C++, donde las clases suelen definirse en archivos de encabezado, se pueden usar construcciones como esta para evitar varias definiciones:

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
    //...
};

#endif // !defined( EXAMPLE_H )
```

El código anterior realiza comprobaciones para ver si se define la constante simbólica `EXAMPLE_H`. Si es así, el archivo ya se ha incluido y no es necesario volver a procesarlo. Si no, se define la constante `EXAMPLE_H` para marcar EXAMPLE.H como ya procesado.

### <a name="__has_include"></a>__has_include

**Visual Studio 2017 versión 15.3 y posteriores:**  Determina si un encabezado de biblioteca está disponible para su inclusión:

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
