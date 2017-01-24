---
title: "void (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "void"
  - "void_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones [C++], void"
  - "punteros, void"
  - "void (palabra clave) [C++]"
ms.assetid: d203edba-38e6-4056-8b89-011437351057
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# void (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se utiliza como un tipo de valor devuelto de función, la palabra clave `void` especifica que la función no devuelve ningún valor.  Cuando se utiliza para la lista de parámetros de una función, void especifica que la función no toma ningún parámetro.  Cuando se utiliza en la declaración de un puntero, void especifica que el puntero es "universal".  
  
 Si el tipo de puntero es **void \***, el puntero puede señalar a cualquier variable que no se declare con la palabra clave **const** o `volatile`.  Un puntero void no se puede desreferenciar a menos que se convierta en otro tipo.  Un puntero void se puede convertir en cualquier otro tipo de puntero de datos.  
  
 Un puntero void puede señalar a una función, pero no a un miembro de clase en C\+\+.  
  
 No se puede declarar una variable de tipo void.  
  
## Ejemplo  
  
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
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Punteros al tipo void](../misc/pointers-to-type-void.md)   
 [Tipos fundamentales](../cpp/fundamental-types-cpp.md)