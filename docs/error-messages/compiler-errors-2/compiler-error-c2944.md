---
title: Error del compilador C2944 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2944
dev_langs:
- C++
helpviewer_keywords:
- C2944
ms.assetid: f209e668-e72f-442a-a438-8c4ff43a404a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c93cde44e7e7816117cc20e4418c57fbf51048d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244272"
---
# <a name="compiler-error-c2944"></a>Error del compilador C2944
'class': el identificador de clase de tipo se redefinió como argumento de valor de una plantilla  
  
 No puede usar una clase genérica o de plantilla, en lugar de un símbolo, como argumento de tipo de plantilla.  
  
 El ejemplo siguiente genera la advertencia C2944:  
  
```  
// C2944.cpp  
// compile with: /c  
template<class T>  
class TC { };   
  
template <int TC<int> > struct X1 { };   // C2944  
  
template <class T > struct X2 {};  
```  
  
 También se puede producir el error C2944 al usar genéricos:  
  
```  
// C2944b.cpp  
// compile with: /clr /c  
generic<class T>  
ref class GC {};  
  
template <int GC<int> > struct X2 { };   // C2944  
template <class T> struct X3 {};   // OK  
```