---
title: "Almacenamiento de uniones | Microsoft Docs"
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
  - "almacenamiento, union"
  - "union (palabra clave) [C]"
  - "union (palabra clave) [C], almacenamiento"
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Almacenamiento de uniones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El almacenamiento asociado a una variable de unión es el almacenamiento necesario para el miembro mayor de la unión.  Cuando se almacena un miembro menor, la variable de unión puede contener espacio de memoria sin usar.  Todos los miembros se almacenan en el mismo espacio de memoria y comienzan en la misma dirección.  El valor almacenado se sobrescribe cada vez que se asigna un valor a un miembro diferente.  Por ejemplo:  
  
```  
union         /* Defines a union named x */  
{  
    char *a, b;  
    float f[20];  
} x;  
```  
  
 Los miembros de la unión `x` son, en orden de declaración, un puntero a un valor `char`, un valor `char` y una matriz de valores **float**.  El almacenamiento asignado para `x` es el almacenamiento necesario para la matriz `f` de 20 elementos, ya que `f` es el miembro más largo de la unión.  Dado que no hay ninguna etiqueta asociada con la unión, su tipo es sin nombre o “anónimo”.  
  
## Vea también  
 [Declaraciones de unión](../c-language/union-declarations.md)