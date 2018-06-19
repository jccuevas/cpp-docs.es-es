---
title: Declaraciones de variables simples | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9bbda7ff9a22a42ce4a6b8c3de10d0d6f0d03f77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389772"
---
# <a name="simple-variable-declarations"></a>Declaraciones de variables simples
La declaración de una variable simple, la forma más sencilla de un declarador directo, especifica el nombre y el tipo de la variable. También especifica la clase de almacenamiento y el tipo de datos de la variable.  
  
 En las declaraciones de variables se requieren clases o tipos de almacenamiento (o ambos). Las variables sin tipo (tales como `var;`) generan advertencias.  
  
## <a name="syntax"></a>Sintaxis  
 `declarator`:  
 *pointer* opt  
  
 *direct-declarator*  
  
 *direct-declarator*:  
 *identifier*  
  
 *identifier*:  
 *nondigit*  
  
 *identifier nondigit*  
  
 *identifier digit*  
  
 Para los tipos aritméticos, de estructura, unión, enumeraciones y vacíos y para tipos representados por nombres de `typedef`, se puede usar declaradores simples en una declaración, puesto que el especificador de tipo proporciona toda la información de tipo. Los tipos de puntero, matriz y función requieren declaradores más complicados.  
  
 Puede utilizar una lista de identificadores separados por comas (**,**) para especificar varias variables en la misma declaración. Todas las variables definidas en la declaración tienen el mismo tipo base. Por ejemplo:  
  
```  
int x, y;        /* Declares two simple variables of type int */  
int const z = 1; /* Declares a constant value of type int */  
```  
  
 Las variables `x` y `y` pueden contener cualquier valor del conjunto definido por el tipo `int` para una implementación concreta. El objeto simple `z` se inicializa con el valor 1 y no es modificable.  
  
 Si la declaración de `z` fuera para una variable estática no inicializada o estuviera en el ámbito de archivo, recibiría un valor inicial de 0 y ese valor no se podría modificar.  
  
```  
unsigned long reply, flag; /* Declares two variables  
                              named reply and flag     */  
```  
  
 En este ejemplo, ambas variables, `reply` y `flag`, son de tipo `unsigned long` y tienen valores enteros sin signo.  
  
## <a name="see-also"></a>Vea también  
 [Declaradores y declaraciones de variables](../c-language/declarators-and-variable-declarations.md)