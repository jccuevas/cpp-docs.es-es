---
title: Error del compilador C2935 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2935
dev_langs:
- C++
helpviewer_keywords:
- C2935
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf3e24aef4cb1111ca6018498a09c28a703aa531
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2935"></a>Error del compilador C2935
'class': el identificador de clase de tipo se ha redefinido como función global.  
  
 No puede usar una clase genérica o de plantilla como función global.  
  
 Este error puede producirse si las llaves no coinciden como es debido.  
  
 El ejemplo siguiente genera la advertencia C2935:  
  
```  
// C2935.cpp  
// compile with: /c  
template<class T>  
struct TC {};   
void TC<int>() {}   // C2935  
  
// OK  
struct TC2 {};   
void TC2() {}  
```  
  
 También se puede producir el error C2935 al usar genéricos:  
  
```  
// C2935b.cpp  
// compile with: /clr /c  
generic<class T>   
ref struct GC { };  
void GC<int>() {}   // C2935  
void GC() {}   // OK  
```