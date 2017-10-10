---
title: C2765 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2765
dev_langs:
- C++
helpviewer_keywords:
- C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f0caf89da3e3bf227d296df36d499b6d19096dfa
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2765"></a>C2765 de Error del compilador
'función': una especialización explícita de una plantilla de función no puede tener ningún argumento predeterminado  
  
 No se permiten argumentos predeterminados en una especialización explícita de una plantilla de función. Para obtener más información, consulte [especialización explícita de plantillas de función](../../cpp/explicit-specialization-of-function-templates.md).  
  
 El ejemplo siguiente genera C2765:  
  
```  
// C2765.cpp  
template<class T> void f(T t) {};  
  
template<> void f<char>(char c = 'a') {}   // C2765  
// try the following line instead  
// template<> void f<char>(char c) {}  
```
