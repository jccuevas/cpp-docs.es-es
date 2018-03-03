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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d94d3a18c02cfe81f6c3ee96635c9388f54308d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
