---
title: Error del compilador C3903 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3903
dev_langs:
- C++
helpviewer_keywords:
- C3903
ms.assetid: cf47d7ad-a3bd-4f75-a253-71586e7a3be6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65f58b402b303a15643c567be9a8a7695e802d96
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3903"></a>Error del compilador C3903
'property': does no se ha establecido o get (método)  
  
 Una propiedad debe tener al menos un `get` o un `set` método. Para obtener más información, consulta [property](../../windows/property-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera C3903:  
  
```  
// C3903.cpp  
// compile with: /clr  
ref class X {  
   property int P {  
      void f(int){}  
      // Add one or both of the following lines.  
      // void set(int){}  
      // int get(){return 0;}  
   };   // C3903  
  
   property double Q[,,,,] {  
      void f(){}  
      // Add one or both of the following lines.  
      // void set(int, char, int, char, double, double){}  
      // double get(int, char, int, char, double){return 1.1;}  
   }   // C3903  
};  
```