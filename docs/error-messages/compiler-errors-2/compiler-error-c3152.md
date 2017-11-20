---
title: Error de compilador Error C3152 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3152
dev_langs: C++
helpviewer_keywords: C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 222a45a8a8820c426902ef3584a3663103b63fa2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3152"></a>Error C3152 de Error del compilador
'construct': 'keyword' solo se puede aplicar a una función de clase, struct o miembro virtual  
  
 Algunas palabras clave solo se pueden aplicar a una clase de C++.  
  
 En el ejemplo siguiente se genera el error C3152 y se muestra cómo corregirlo.  
  
```  
// C3152.cpp  
// compile with: /clr /c  
ref class C {  
   int (*pfn)() sealed;   // C3152  
   virtual int g() sealed;   // OK  
};  
```  
