---
title: Advertencia de compilador advertencia C4936 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4936
dev_langs:
- C++
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 58d702067c186eeeea94768a03836b64577961ca
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-c4936"></a>Advertencia del compilador C4936
__declspec se admite solamente cuando se compila con /clr o /clr:pure  
  
 El **/CLR: pure** opción del compilador está desusada en Visual Studio 2015.  
  
 Un `__declspec` se utilizó el modificador pero que `__declspec` modificador sólo es válido cuando se compila con uno de los [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opciones.  
  
 Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [proceso](../../cpp/process.md).  
  
 La advertencia C4936 siempre se emite como error.  Puede deshabilitar la advertencia C4936 con el [advertencia](../../preprocessor/warning.md) pragma.  
  
 El ejemplo siguiente genera la advertencia C4936:  
  
```  
// C4936.cpp  
// compile with: /c  
// #pragma warning (disable : 4936)  
__declspec(process) int i;   // C4936  
__declspec(appdomain) int j;   // C4936  
```
