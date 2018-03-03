---
title: Compilador advertencia (nivel 3) C4290 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4290
dev_langs:
- C++
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f70a278cb3e660e89e1aba067cab9c20aacf8f62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4290"></a>Advertencia del compilador (nivel 3) C4290
Especificación de excepciones de C++ ignoran, excepto to indicar que una función no es __declspec (nothrow)  
  
 Una función se declara mediante la especificación de excepción, que Visual C++ admite pero no implementa. Con excepción de las especificaciones que se omiten durante la compilación que necesite volver a compilar el código y vinculados para que pueda reutilizarse en el futuro versiones que admiten las especificaciones de excepción.  
  
 Para obtener más información, consulte [especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md) .  
  
 Puede evitar esta advertencia mediante la [advertencia](../../preprocessor/warning.md) pragma:  
  
```  
#pragma warning( disable : 4290 )  
```  
  
 El ejemplo de código siguiente genera C4290:  
  
```  
// C4290.cpp  
// compile with: /EHs /W3 /c  
void f1(void) throw(int) {}   // C4290  
  
// OK  
void f2(void) throw() {}  
void f3(void) throw(...) {}  
```