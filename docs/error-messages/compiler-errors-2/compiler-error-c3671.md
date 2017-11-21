---
title: Error del compilador C3671 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3671
dev_langs: C++
helpviewer_keywords: C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b64c8be94bc6eb89fea04d7edee342e0015b8a9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3671"></a>Error del compilador C3671
'función_1': función no reemplaza 'función_2'  
  
 Cuando se usa la sintaxis de reemplazo explícito, el compilador genera un error si no se reemplaza una función.  Vea [reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3671.  
  
```  
// C3671.cpp  
// compile with: /clr /c  
ref struct S {  
   virtual void f();  
};  
  
ref struct S1 : S {  
   virtual void f(int) new sealed = S::f;   // C3671  
   virtual void f() new sealed = S::f;  
};  
```