---
title: Error del compilador C3366 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3366
dev_langs:
- C++
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b862e606b86eca0a7eb7f2ad1e91f2776c8c0b23
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3366"></a>Error del compilador C3366
'variable': los miembros de datos estáticos de administrada o WinRTtypes deben estar definidos dentro de la definición de clase  
  
 Ha intentado hacer referencia a un miembro estático de una clase o interfaz .NET o WinRT fuera de la definición de esa clase o interfaz.  
  
 El compilador necesita conocer la definición completa de la clase (para emitir los metadatos después de un paso) y requiere que los miembros de datos estáticos se inicialicen en la clase.  
  
 Por ejemplo, en el ejemplo siguiente se genera el error C3366 y se muestra cómo corregirlo:  
  
```  
// C3366.cpp  
// compile with: /clr /c  
ref class X {  
   public:  
   static int i;   // initialize i here to avoid C3366  
};  
  
int X::i = 5;      // C3366  
```  

