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
ms.openlocfilehash: a4342c749c5db4d66f206209a146ad7d7aef7041
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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