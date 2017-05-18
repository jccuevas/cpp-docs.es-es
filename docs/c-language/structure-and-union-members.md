---
title: "Miembros de estructura y de unión | Microsoft Docs"
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
- member-selection operators
- structure members, referencing
- -> operator, structure and union members
- dot operator (.)
- referencing structure members
- . operator
- operators [C], member selection
- structure member selection
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
caps.latest.revision: 8
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 31118df209db98435a3b9cfb0c38e17dbd818d01
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="structure-and-union-members"></a>Miembros de estructura y de unión
Una expresión de selección de miembro (“member-selection expression”) hace referencia a miembros de estructuras y uniones. Tal expresión tiene el valor y el tipo del miembro seleccionado.  
  
```  
  
postfix-expression  
.  
identifier  
postfix-expression  
->  
identifier  
  
```  
  
 En esta lista se describen las dos formas de expresiones de selección de miembro:  
  
1.  En la primera forma, *postfix-expression* representa un valor de tipo `struct` o **union**, e *identifier* nombra un miembro de la estructura o unión especificadas. El valor de la operación es el de *identifier* y es un valor L si *postfix-expression* es un valor L. Vea [Expresiones de valor L y de valor R](../c-language/l-value-and-r-value-expressions.md) para obtener más información.  
  
2.  En la segunda forma, *postfix-expression* representa un puntero a una estructura o unión, e *identifier* nombra un miembro de la estructura o unión especificadas. El valor es el de *identifier* y es un valor L.  
  
 Las dos formas de expresiones de selección de miembros tienen efectos similares.  
  
 De hecho, una expresión que contenga el operador de selección de miembro (**->**) es una versión abreviada de una expresión que usa el punto (**.**) si la expresión anterior al punto consta del operador de direccionamiento indirecto (**\***) aplicado a un valor de puntero. Por lo tanto,  
  
```  
  
expression  
->  
identifier  
  
```  
  
 es equivalente a  
  
```  
  
(*  
expression  
) .  
identifier  
  
```  
  
 cuando *expression* es un valor de puntero.  
  
## <a name="examples"></a>Ejemplos  
 Los ejemplos siguientes hacen referencia a esta declaración de estructura. Para obtener información sobre el operador de direccionamiento indirecto (**\***) usado en estos ejemplos, vea [Direccionamiento indirecto y dirección de operadores](../c-language/indirection-and-address-of-operators.md).  
  
```  
struct pair   
{  
    int a;  
    int b;  
    struct pair *sp;  
} item, list[10];  
```  
  
 Una expresión de selección de miembro para la estructura `item` tiene el siguiente aspecto:  
  
```  
item.sp = &item;  
```  
  
 En el ejemplo anterior, la dirección de la estructura `item` se asigna al miembro `sp` de la estructura. Esto significa que `item` contiene un puntero a sí mismo.  
  
```  
(item.sp)->a = 24;  
```  
  
 En este ejemplo, la expresión de puntero `item.sp` se usa con el operador de selección de miembro (**->**) para asignar un valor al miembro `a`.  
  
```  
list[8].b = 12;  
```  
  
 Esta instrucción muestra cómo seleccionar un miembro de estructura individual de una matriz de estructuras.  
  
## <a name="see-also"></a>Vea también  
 [Operadores de acceso a miembros: . y ->](../cpp/member-access-operators-dot-and.md)
