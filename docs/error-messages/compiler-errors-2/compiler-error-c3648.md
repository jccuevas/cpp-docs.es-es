---
title: Error del compilador C3648 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3648
dev_langs:
- C++
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1836df0658dd4a3d7391d0d35c36bf8ed9221a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3648"></a>Error del compilador C3648
Esta sintaxis de reemplazo explícita requiere/CLR: oldSyntax  
  
Cuando se compila con la última sintaxis administrada, el compilador encontró explícito invalidar sintaxis para las versiones anteriores que ya no se admite.  
  
Para obtener más información, consulte [reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3648:  
  
```  
// C3648.cpp  
// compile with: /clr  
public interface struct I {  
   void f();  
};  
  
public ref struct R : I {  
   virtual void I::f() {}   // C3648  
   // try the following line instead  
   // virtual void f() = I::f{}  
};  
```