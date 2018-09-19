---
title: Especificadores de tipos de C | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16c204636baf87cd88f80294b1f413cacc9f5ddc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764269"
---
# <a name="c-type-specifiers"></a>Especificadores de tipos de C

Los especificadores de tipo en las declaraciones definen el tipo de una declaración de variable o de función.

## <a name="syntax"></a>Sintaxis

*type-specifier*:  
&nbsp;&nbsp;&nbsp;&nbsp;**void**  
&nbsp;&nbsp;&nbsp;&nbsp;**char**  
&nbsp;&nbsp;&nbsp;&nbsp;**short**  
&nbsp;&nbsp;&nbsp;&nbsp;**int**  
&nbsp;&nbsp;&nbsp;&nbsp;**long**  
&nbsp;&nbsp;&nbsp;&nbsp;**float**  
&nbsp;&nbsp;&nbsp;&nbsp;**double**  
&nbsp;&nbsp;&nbsp;&nbsp;**signed**  
&nbsp;&nbsp;&nbsp;&nbsp;**unsigned**  
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*  
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*  
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*  

Los tipos **signed char**, **signed int**, **signed short int** y **signed long int**, así como sus homólogos **unsigned** y **enum**, se denominan tipos *enteros*. Los especificadores de tipo **float**, **double** y **long double** se conocen como tipos *flotantes* o de *punto flotante*. Se puede utilizar cualquier especificador de tipo entero o de punto flotante en una declaración de variable o de función. Si en una declaración no se proporciona *type-specifier*, se considera que es **int**.

Las palabras clave opcionales **signed** y **unsigned** pueden ir precedidas o seguidas de cualquiera de los tipos enteros, excepto **enum**. También se pueden utilizar solas como especificadores de tipo, en cuyo caso se entienden como **signed int** y **unsigned int**, respectivamente. Cuando la palabra clave **int** se usa sola, se da por supuesto que es **signed**. Cuando las palabras clave **long** y **short** se utilizan solas, se entienden como **long int** y **short int**.

Los tipos de enumeración se consideran tipos básicos. Los especificadores para los tipos de enumeración se describen en [Declaraciones de enumeración](../c-language/c-enumeration-declarations.md).

La palabra clave **void** tiene tres usos: especificar un tipo de valor devuelto de función, especificar una lista de tipos de argumento para una función que no toma ningún argumento y especificar un puntero para un tipo sin especificar. El tipo **void** se puede utilizar para declarar funciones que no devuelven ningún valor o para declarar un puntero para un tipo sin especificar. Vea [Argumentos](../c-language/arguments.md) para obtener información sobre el tipo **void** cuando aparece solo entre paréntesis después de un nombre de función.

**Específicos de Microsoft**

La comprobación de tipos es ahora compatible con ANSI, lo que significa que **short** e **int** son tipos distintos. Por ejemplo, esto es una nueva definición en el compilador de Microsoft C que se aceptaba en versiones anteriores del compilador.

```C
int   myfunc();
short myfunc();
```

En el ejemplo siguiente también se genera una advertencia sobre el direccionamiento indirecto a tipos diferentes:

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

El compilador de Microsoft C también genera advertencias para las diferencias de signo. Por ejemplo:

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

Las expresiones de tipo **void** se evalúan para ver si tienen efectos secundarios. No se puede utilizar el valor (inexistente) de una expresión que tiene el tipo **void** de ninguna forma, ni puede convertirse una expresión **void**, mediante conversión implícita o explícita, a ningún tipo, excepto **void**. Si utiliza una expresión de cualquier otro tipo en un contexto en el que se requiera una expresión **void**, su valor quedará descartado.

Por conformidad con la especificación ANSI, <strong>void\*\*</strong> no se puede utilizar como <strong>int\*\*</strong>. Solo **void**<strong>\*</strong> se puede utilizar como puntero a un tipo sin especificar.

**FIN de Específicos de Microsoft**

Se pueden crear especificadores de tipo adicionales con declaraciones **typedef**, como se describe en [Declaraciones typedef](../c-language/typedef-declarations.md). Vea [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md) para obtener información sobre el tamaño de cada tipo.

## <a name="see-also"></a>Vea también

[Declaraciones y tipos](../c-language/declarations-and-types.md)  
