---
title: Error del compilador C3656 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3656
dev_langs:
- C++
helpviewer_keywords:
- C3656
ms.assetid: 88965d85-73b0-4b35-8020-0650c9c94cd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f361cc4356989b22b973972a506b28e97f39cac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263991"
---
# <a name="compiler-error-c3656"></a>Error del compilador C3656
'override': invalidar no se puede repetir el especificador  
  
 Una palabra clave de reemplazo explícito solo puede especificarse una vez. Para obtener más información, consulte [reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera C3656:  
  
```  
// C3656.cpp  
// compile with: /clr /c  
public interface struct O {  
   int f();  
};  
  
public ref struct V : O {  
   int f() override override { return 0; }   // C3656  
   // try the following line instead  
   // int f() override { return 0; }  
};  
```