---
title: void (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- void_cpp
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbb46302c2ae8834ab9a2a626a3bfb77c41996a2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461483"
---
# <a name="void-c"></a>void (C++)
Cuando se usa como un tipo de valor devuelto de función, el **void** palabra clave especifica que la función no devuelve un valor. Cuando se utiliza para la lista de parámetros de una función, void especifica que la función no toma ningún parámetro. Cuando se utiliza en la declaración de un puntero, void especifica que el puntero es "universal".  
  
 Si es de tipo de puntero `void *`, el puntero puede señalar a cualquier variable que no se ha declarado con el **const** o **volátil** palabra clave. Un puntero void no se puede desreferenciar a menos que se convierta en otro tipo. Un puntero void se puede convertir en cualquier otro tipo de puntero de datos.  
  
 Un puntero void puede señalar a una función, pero no a un miembro de clase en C++.  
  
 No se puede declarar una variable de tipo void.  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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