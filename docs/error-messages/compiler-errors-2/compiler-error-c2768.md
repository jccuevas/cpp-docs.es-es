---
title: C2768 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee0fd3fa213639e70199cfe5653ee2034bc39b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2768"></a>C2768 de Error del compilador
'función': uso no válido de argumentos de plantilla explícitos  
  
 El compilador no pudo determinar si una definición de función debía para ser una especialización explícita de una plantilla de función o si la definición de función debía ser para una nueva función.  
  
 Este error se introdujo en Visual Studio .NET 2003, como parte de las mejoras de conformidad del compilador.  
  
 El ejemplo siguiente genera C2768:  
  
```  
// C2768.cpp  
template<typename T>  
void f(T) {}  
  
void f<int>(int) {}   // C2768  
  
// an explicit specialization  
template<>  
void f<int>(int) {}   
  
// global nontemplate function overload  
void f(int) {}  
```