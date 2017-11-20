---
title: Error del compilador C3656 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3656
dev_langs: C++
helpviewer_keywords: C3656
ms.assetid: 88965d85-73b0-4b35-8020-0650c9c94cd8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bbb82f1684da4c7a3fe659f3892e7b1004a7f814
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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