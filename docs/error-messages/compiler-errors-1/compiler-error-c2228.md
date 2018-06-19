---
title: Error del compilador C2228 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2228
dev_langs:
- C++
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 969f622877c60bdc340dedf8a2416ac56b2ad0e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171030"
---
# <a name="compiler-error-c2228"></a>Error del compilador C2228
a la izquierda de '.identifier' debe haber class/struct/union  
  
 El operando situado a la izquierda del punto (.) no es una clase, estructura o unión.  
  
 El ejemplo siguiente genera la advertencia C2228:  
  
```  
// C2228.cpp  
int i;  
struct S {  
public:  
    int member;  
} s, *ps = &s;  
  
int main() {  
   i.member = 0;   // C2228 i is not a class type  
   ps.member = 0;  // C2228 ps is a pointer to a structure  
  
   s.member = 0;   // s is a structure type  
   ps->member = 0; // ps points to a structure S  
}  
```  
  
 También verá este error si usa una sintaxis incorrecta al usar extensiones administradas. Mientras que en otros lenguajes de Visual Studio, puede usar el operador punto para tener acceso a un miembro de una clase administrada, un puntero al objeto en C++ significa que debe usar el operador -> para obtener acceso al miembro:  
  
 Erróneo: `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`  
  
 Correcto: `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`