---
title: "Miembros de estructura y de uni&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - ". (operador)"
  - "-> (operador), miembros de estructura y de unión"
  - "operador de punto (.)"
  - "operadores de selección de miembros"
  - "operadores [C], selección de miembro"
  - "hacer referencia a miembros de estructura"
  - "selección de miembro de estructura"
  - "miembros de estructura, hacer referencia"
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Miembros de estructura y de uni&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una expresión de selección de miembro \(“member\-selection expression”\) hace referencia a miembros de estructuras y uniones.  Tal expresión tiene el valor y el tipo del miembro seleccionado.  
  
```  
  
        postfix-expression . identifier  
postfix-expression –> identifier  
```  
  
 En esta lista se describen las dos formas de expresiones de selección de miembro:  
  
1.  En la primera forma, *postfix\-expression* representa un valor de tipo `struct` o **union**, e *identifier* nombra un miembro de la estructura o unión especificadas.  El valor de la operación es el de *identifier* y es un valor L si *postfix\-expression* es un valor L.  Vea [Expresiones de valor L y de valor R](../c-language/l-value-and-r-value-expressions.md) para obtener más información.  
  
2.  En la segunda forma, *postfix\-expression* representa un puntero a una estructura o unión, e *identifier* nombra un miembro de la estructura o unión especificadas.  El valor es el de *identifier* y es un valor L.  
  
 Las dos formas de expresiones de selección de miembros tienen efectos similares.  
  
 De hecho, una expresión que contenga el operador de selección de miembro \(**–\>**\) es una versión abreviada de una expresión que usa el punto \(**.**\) si la expresión anterior al punto consta del operador de direccionamiento indirecto \(**\***\) aplicado a un valor de puntero.  Por lo tanto,  
  
```  
  
expression –> identifier  
```  
  
 es equivalente a  
  
```  
  
(*  
expression  
) . identifier  
```  
  
 cuando *expression* es un valor de puntero.  
  
## Ejemplos  
 Los ejemplos siguientes hacen referencia a esta declaración de estructura.  Para obtener información sobre el operador de direccionamiento indirecto \(**\***\) utilizado en estos ejemplos, vea [Direccionamiento indirecto y dirección de operadores](../c-language/indirection-and-address-of-operators.md).  
  
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
  
 En el ejemplo anterior, la dirección de la estructura `item` se asigna al miembro `sp` de la estructura.  Esto significa que `item` contiene un puntero a sí mismo.  
  
```  
(item.sp)–>a = 24;  
```  
  
 En este ejemplo, la expresión de puntero `item.sp` se usa con el operador de selección de miembro \(**–\>**\) para asignar un valor al miembro `a`.  
  
```  
list[8].b = 12;  
```  
  
 Esta instrucción muestra cómo seleccionar un miembro de estructura individual de una matriz de estructuras.  
  
## Vea también  
 [Operadores de acceso a miembros: . y \-\>](../cpp/member-access-operators-dot-and.md)