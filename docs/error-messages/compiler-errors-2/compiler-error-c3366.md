---
title: Error del compilador C3366 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3366
dev_langs:
- C++
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c26bfbb5d66ad22484184bd361f14004ed8aa30c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254279"
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
