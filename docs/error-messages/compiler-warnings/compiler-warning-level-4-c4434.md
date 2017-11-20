---
title: Compilador advertencia (nivel 4) C4434 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4434
dev_langs: C++
helpviewer_keywords: C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b400ef921cd310cd27b5b4a65867ab7d27255a3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4434"></a>Advertencia del compilador (nivel 4) C4434
un constructor de clase debe tener accesibilidad privada; se cambiará a acceso privado  
  
 La advertencia C4434 indica que el compilador ha cambiado la accesibilidad de un constructor estático. Los constructores estáticos deben tener accesibilidad privada, ya que están concebidos para que sólo los llame Common Language Runtime. Para obtener más información, consulte [constructores estáticos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4434.  
  
```  
// C4434.cpp  
// compile with: /W4 /c /clr  
public ref struct R {  
   static R(){}   // C4434  
};  
```