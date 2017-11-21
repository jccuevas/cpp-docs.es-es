---
title: Error del compilador C3387 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3387
dev_langs: C++
helpviewer_keywords: C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 79b38cd1793509c92ec2d2941fbb3eb2e7121ee7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3387"></a>Error del compilador C3387
'member': __declspec (dllexport) /\__declspec (dllimport) no se puede aplicar a un miembro de una clase administrada o tipo WinRT  
  
 El `dllimport` y [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` modificadores no son válidos en miembros de una clase administrada o de tipo en tiempo de ejecución de Windows.  
  
 El ejemplo siguiente genera el error C3387 y muestra cómo corregirlo:  
  
```  
// C3387a.cpp  
// compile with: /clr /c  
ref class X2 {  
   void __declspec(dllexport) mf() {   // C3387  
   // try the following line instead  
   // void mf() {  
   }  
};  
```