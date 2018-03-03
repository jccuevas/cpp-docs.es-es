---
title: Error del compilador C3898 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3898
dev_langs:
- C++
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b961c7eb788d1938263025e442a3e336a8ce3567
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3898"></a>Error del compilador C3898
'var': los miembros de datos de tipo sólo pueden ser miembros de tipos administrados  
  
 Un [initonly](../../dotnet/initonly-cpp-cli.md) miembro de datos se ha declarado en una clase nativa.  Un `initonly` miembro de datos solo puede declararse en una clase CLR.  
  
 El ejemplo siguiente genera C3898:  
  
```  
// C3898.cpp  
// compile with: /clr  
struct Y1 {  
   initonly  
   static int data_var = 9;   // C3898  
};  
```  
  
 Posible resolución:  
  
```  
// C3898b.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   initonly  
   static int data_var = 9;  
};  
```