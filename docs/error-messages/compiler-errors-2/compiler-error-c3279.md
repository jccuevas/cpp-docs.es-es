---
title: Error del compilador C3279 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3279
dev_langs:
- C++
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 16bb13d226b6d4d5d5846f8302070bf0c9579cfb
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3279"></a>Error del compilador C3279
no se permiten especializaciones parciales o explícitas ni creaciones de instancias explícitas de plantillas de clase declaradas en el espacio de nombres cli  
  
 El espacio de nombres `cli` está definido por Microsoft y contiene pseudoplantillas. El compilador de Visual C++ no permite las especializaciones definidas por el usuario, parciales, explícitas ni creaciones de instancias explícitas de plantillas de clase en este espacio de nombres.  
  
 El ejemplo siguiente genera la advertencia C3279:  
  
```  
// C3279.cpp  
// compile with: /clr  
namespace cli {  
   template <> ref class array<int> {};   // C3279  
   template <typename T> ref class array<T, 2> {};   // C3279  
}  
```
