---
title: Error del compilador C3662 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3662
dev_langs: C++
helpviewer_keywords: C3662
ms.assetid: 61bd3e41-a86b-42c0-be89-d992d3906ff1
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f0068080f4cb1b2b25e350acd331898d6c49a3f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3662"></a>Error del compilador C3662
'miembro': el especificador de invalidación 'especificador' solamente se permite en funciones miembro de clases administradas o de WinRT.  
  
 Se usó un especificador de invalidación en un miembro de tipo nativo, lo que no está permitido.  
  
 Para obtener más información, consulte [reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C3662.  
  
```  
// C3662.cpp  
// compile with: /clr /c  
struct S {  
   virtual void f();  
};  
  
struct S1 : S {  
   virtual void f() new;   // C3662  
};  
  
ref struct T {  
   virtual void f();  
};  
  
ref struct T1 : T {  
   virtual void f() new;   // OK  
};  
```