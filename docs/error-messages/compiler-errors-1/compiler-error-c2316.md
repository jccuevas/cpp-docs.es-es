---
title: Error del compilador C2316 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2316
dev_langs:
- C++
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8fa8426f89d0d61ff32facb3ab0b15ac5b770e94
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2316"></a>Error del compilador C2316

> '*excepción*': no se puede detectar porque es inaccesible al destructor o al constructor de copias  
  
Se detectó una excepción por valor o por referencia, pero no se ha podido obtener acceso al constructor de copias o al operador de asignación.  
  
Este código se aceptaba en versiones de Visual C++ antes de Visual Studio 2003, pero ahora produce un error.  
  
Los cambios de conformidad en Visual Studio 2015 realizan este error se aplica a las instrucciones catch incorrecta de excepciones de MFC derivadas de `CException`. Dado que `CException` tiene un constructor de copias privado heredados, la clase y sus derivados son no se puede copiar y no se pueden pasar por valor, lo que también significa que no se puede detectar por valor. Instrucciones que detecta las excepciones de MFC valor que previamente se llevó a las excepciones no detectadas en tiempo de ejecución de captura, pero ahora el compilador identifica correctamente esta situación y los informes de error advertencia C2316. Para corregir este problema, se recomienda que usar las macros MFC TRY/CATCH en lugar de escriben sus propios controladores de excepciones, pero si no es adecuado para el código, detectar excepciones de MFC por referencia en su lugar.   
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C2316:  
  
```  
// C2316.cpp  
// compile with: /EHsc  
#include <stdio.h>  
  
extern "C" int printf_s(const char*, ...);  
  
struct B   
{  
public:  
    B() {}  
    // Delete the following line to resolve.  
private:  
    // copy constructor  
    B(const B&)   
    {  
    }  
};  
  
void f(const B&)   
{  
}  
  
int main()   
{  
    try   
    {  
        B aB;  
        f(aB);  
    }  
    catch (B b) {   // C2316  
        printf_s("Caught an exception!\n");     
    }  
}  
```
