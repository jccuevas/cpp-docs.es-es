---
title: "Especialización explícita de plantillas de función | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
caps.latest.revision: 7
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
ms.translationtype: HT
ms.sourcegitcommit: f460497071445cff87308fa9bf6e0d43c6f13a3e
ms.openlocfilehash: c5caabae41383edbdc92806249026ce8a0daa5d5
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="explicit-specialization-of-function-templates"></a>Especialización explícita de las plantillas de función
Con una plantilla de función, puede definir un comportamiento especial para un tipo específico si proporciona una especialización explícita (reemplazo) de la plantilla de función de ese tipo. Por ejemplo:  
  
```cpp
template<> void MySwap(double a, double b);  
```  
  
 Esta declaración permite definir una función diferente para **doble** variables. Al igual que no es de plantilla funciones, conversiones de tipos estándar (por ejemplo, promover una variable de tipo **float** a **doble**) se aplican.  
  
## <a name="example"></a>Ejemplo  
  
```cpp
// explicit_specialization.cpp  
template<class T> void f(T t)  
{  
};  
  
// Explicit specialization of f with 'char' with the  
// template argument explicitly specified:  
//  
template<> void f<char>(char c)  
{  
}  
  
// Explicit specialization of f with 'double' with the  
// template argument deduced:  
//  
template<> void f(double d)  
{  
}  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de función](../cpp/function-templates.md)

