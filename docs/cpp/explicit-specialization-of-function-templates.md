---
title: Especialización explícita de plantillas de función | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e35eda35a7d2474826ce151292121be224955420
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410738"
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
