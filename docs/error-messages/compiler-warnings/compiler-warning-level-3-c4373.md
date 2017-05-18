---
title: Compilador advertencia (nivel 3) C4373 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4373
dev_langs:
- C++
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
caps.latest.revision: 7
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
ms.openlocfilehash: 36d4491f8a621f1ee97de9682faf94a26a89fa70
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4373"></a>Advertencia del compilador (nivel 3) C4373
'%$S': la función virtual invalida '%$pS'; las versiones anteriores del compilador no se reemplazaron cuando los parámetros solo se diferenciaban en los calificadores const y volatile  
  
 La aplicación contiene un método en una clase derivada que reemplaza un método virtual en una clase base y los parámetros en el método de reemplazo difieren solo un [const](../../cpp/const-cpp.md) o [volátiles](../../cpp/volatile-cpp.md) calificador de los parámetros del método virtual. Esto significa que el compilador debe enlazar una referencia a función con el método en la clase derivada o base.  
  
 Las versiones del compilador anteriores a [!INCLUDE[cpp_orcas_long](../../cpp/includes/cpp_orcas_long_md.md)] enlazar la función con el método de la clase base, a continuación, emitir un mensaje de advertencia. Las versiones posteriores del compilador omiten el calificador `const` o `volatile` , enlazan la función con el método de la clase derivada y después emiten la advertencia `C4373`. Este último comportamiento cumple con el estándar de C++.  
  
## <a name="example"></a>Ejemplo  
 El siguiente código de ejemplo genera la advertencia C4373.  
  
```  
// c4373.cpp  
// compile with: /c /W3  
#include <stdio.h>  
struct Base  
{  
    virtual void f(int i) {  
        printf("base\n");  
    }  
};  
struct Derived : Base  
{  
    void f(const int i) {  // C4373  
        printf("derived\n");  
    }  
};  
void main()  
{  
    Derived d;  
    Base* p = &d;  
    p->f(1);  
}  
```  
  
```Output  
derived  
```
