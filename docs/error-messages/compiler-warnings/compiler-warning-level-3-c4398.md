---
title: Compilador advertencia (nivel 3) C4398 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4398
dev_langs:
- C++
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
caps.latest.revision: 6
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 18270bb89bcc5d1855750c572a5b6fb9e51c2ba3
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4398"></a>Advertencia del compilador (nivel 3) C4398
'variable': objeto global por proceso no funcionen correctamente con varios dominios de aplicación; Considere el uso de __declspec (AppDomain)  
  
 Una función virtual con [__clrcall](../../cpp/clrcall.md) convención de llamada en un tipo nativo produce la creación de una por vtable de dominio de aplicación. Este tipo de variable no puede corregir correctamente cuando se utiliza en varios dominios de aplicación.  
  
 Puede resolver esta advertencia marque explícitamente la variable `__declspec(appdomain)`. En las versiones de Visual Studio antes de 2017 de Visual Studio, puede resolver esta advertencia, compile con **/CLR: pure**, que hace variables globales por appdomain de forma predeterminada.  
  
 Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [dominios de aplicación y Visual C++](../../dotnet/application-domains-and-visual-cpp.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4398.  
  
```  
// C4398.cpp  
// compile with: /clr /W3 /c  
struct S {  
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall  
};  
  
S glob_s;   // C4398  
__declspec(appdomain) S glob_s2;   // OK  
```
