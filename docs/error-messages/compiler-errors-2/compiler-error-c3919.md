---
title: Error del compilador C3919 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3919
dev_langs: C++
helpviewer_keywords: C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 26e3b3fed712c1d738d214ab5f12c9572bab7206
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3919"></a>Error del compilador C3919
'método del evento': función debe tener un tipo 'type'  
  
 No se declaró correctamente un método de descriptor de acceso de eventos.  
  
 Para obtener más información acerca de los eventos, vea [eventos](../../windows/event-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera C3919:  
  
```  
// C3919.cpp  
// compile with: /clr /c  
using namespace System;  
delegate void D(String^);  
ref class R {  
   event D^ e {  
      int add(int);   // C3919  
      int remove(int);   // C3919  
  
      void add(D^);   // OK  
      void remove(D^);   // OK  
   }  
};  
```