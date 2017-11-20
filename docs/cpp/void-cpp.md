---
title: void (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: void_cpp
dev_langs: C++
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5ec762d15c878df4bcde01284f1b10783bff7e3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="void-c"></a>void (C++)
Cuando se utiliza como un tipo de valor devuelto de función, la palabra clave `void` especifica que la función no devuelve ningún valor. Cuando se utiliza para la lista de parámetros de una función, void especifica que la función no toma ningún parámetro. Cuando se utiliza en la declaración de un puntero, void especifica que el puntero es "universal".  
  
 Si es de tipo de puntero **void \*** , el puntero puede señalar a cualquier variable que no se ha declarado con la **const** o `volatile` (palabra clave). Un puntero void no se puede desreferenciar a menos que se convierta en otro tipo. Un puntero void se puede convertir en cualquier otro tipo de puntero de datos.  
  
 Un puntero void puede señalar a una función, pero no a un miembro de clase en C++.  
  
 No se puede declarar una variable de tipo void.  
  
## <a name="example"></a>Ejemplo  
  
```  
// void.cpp  
void vobject;   // C2182  
void *pv;   // okay  
int *pint; int i;  
int main() {  
   pv = &i;  
   // Cast optional in C required in C++  
   pint = (int *)pv;  
}   
```  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Tipos fundamentales](../cpp/fundamental-types-cpp.md)