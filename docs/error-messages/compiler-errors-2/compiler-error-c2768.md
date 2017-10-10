---
title: C2768 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 79693c3d7b337302698d7854b5cd447ce7c68334
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

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
