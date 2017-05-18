---
title: Error del compilador C2228 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2228
dev_langs:
- C++
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 39bbed326de5fc0a367e9b7693d3975b766e9bfc
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

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
  
 Problema:`String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`  
  
 Correcto:`String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`
