---
title: Declaraciones de variables simples | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 03d3939ef04a6a1a8bc5e3cd3ec5bfe56236ca0f
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

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
