---
title: Tipo de valor devuelto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08c81333d599411b180ebf5f0a00e1ab61536903
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076858"
---
# <a name="return-type"></a>Tipo devuelto

El tipo de valor devuelto de una función establece el tamaño y el tipo de valor devuelto por la función y corresponde al especificador de tipo en la sintaxis siguiente:

## <a name="syntax"></a>Sintaxis

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* es específico de Microsoft \*/

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*type-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int8** /\* Específico de Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int16** /\* Específico de Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int32** /\* Específico de Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int64** /\* Específico de Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**signed**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**unsigned**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

El elemento *type-specifier* puede especificar cualquier tipo fundamental, de estructura o de unión. Si no incluye *type-specifier*, se presupone el tipo de valor devuelto `int`.

El tipo de valor devuelto especificado en la definición de la función debe coincidir con el tipo de valor devuelto en las declaraciones de la función que se encuentren en cualquier parte del programa. Una función devuelve un valor cuando se ejecuta una instrucción `return` que contiene una expresión. La expresión se evalúa, se convierte al tipo de valor devuelto si es necesario y se regresa al punto donde se llamó a la función. Si una función se declara con el tipo de valor devuelto `void`, una instrucción return que contiene una expresión genera una advertencia y la expresión no se evalúa.

En los ejemplos siguientes se muestran los valores devueltos de la función.

```C
typedef struct
{
    char name[20];
    int id;
    long class;
} STUDENT;

/* Return type is STUDENT: */

STUDENT sortstu( STUDENT a, STUDENT b )
{
    return ( (a.id < b.id) ? a : b );
}
```

En este ejemplo se define el tipo `STUDENT` con una declaración de `typedef` y se define la función `sortstu` para tener el tipo de valor devuelto `STUDENT`. La función selecciona y devuelve uno de sus dos argumentos de estructura. En las llamadas posteriores a la función, el compilador comprueba que los tipos de argumentos son `STUDENT`.

> [!NOTE]
> Se podría conseguir una mayor eficacia pasando punteros a la estructura, en lugar de la estructura completa.

```C
char *smallstr( char s1[], char s2[] )
{
    int i;

    i = 0;
    while ( s1[i] != '\0' && s2[i] != '\0' )
        i++;
    if ( s1[i] == '\0' )
        return ( s1 );
    else
        return ( s2 );
}
```

En este ejemplo se define una función que devuelve un puntero a una matriz de caracteres. La función toma dos matrices de caracteres (cadenas) como argumentos y devuelve un puntero a la cadena más corta. Un puntero a una matriz apunta al primero de los elementos de la matriz y tiene su tipo; por tanto, el tipo de valor devuelto de la función es un puntero al tipo `char`.

No necesita declarar funciones con el tipo de valor devuelto `int` antes de llamarlas, aunque se recomienda usar prototipos para que se pueda comprobar el tipo correcto de los argumentos y valores devueltos.

## <a name="see-also"></a>Vea también

[Definiciones de función de C](../c-language/c-function-definitions.md)