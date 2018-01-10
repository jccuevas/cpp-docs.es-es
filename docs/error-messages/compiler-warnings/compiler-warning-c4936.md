---
title: Advertencia del compilador C4936 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4936
dev_langs: C++
helpviewer_keywords: C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 995cd7b2b774b768d6bccf10ddcec18101580e74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4936"></a>Advertencia del compilador C4936
__declspec se admite solamente cuando se compila con /clr o /clr:pure  
  
 El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015.  
  
 Se utilizó un modificador `__declspec` , pero ese modificador `__declspec` solo es válido cuando se compila con una de las opciones [/clr](../../build/reference/clr-common-language-runtime-compilation.md) .  
  
 Para más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).  
  
 La advertencia C4936 siempre se emite como error.  Puede deshabilitar la advertencia C4936 con la pragma [warning](../../preprocessor/warning.md) .  
  
 El ejemplo siguiente genera la advertencia C4936:  
  
```  
// C4936.cpp  
// compile with: /c  
// #pragma warning (disable : 4936)  
__declspec(process) int i;   // C4936  
__declspec(appdomain) int j;   // C4936  
```