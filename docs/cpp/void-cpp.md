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
ms.workload: cplusplus
ms.openlocfilehash: a800aca290a178e3b193c245df515385311b5593
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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