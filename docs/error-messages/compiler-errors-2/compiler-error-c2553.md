---
title: Error del compilador C2553 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2553
dev_langs:
- C++
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cfb09f2701b418ab5570641a78c465ff72ed943
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232539"
---
# <a name="compiler-error-c2553"></a>Error del compilador C2553
'función_base': función virtual de reemplazo devolver tipo difiere de 'función_de_reemplazo'  
  
 Una función en una clase derivada intentó reemplazar una función virtual en una clase base, pero la función de clase derivada no tenía el mismo tipo de valor devuelto que la función de clase base.  Una firma de la función de reemplazo debe coincidir con la firma de la función que se va a invalidar.  
  
 El ejemplo siguiente genera C2553:  
  
```  
// C2553.cpp  
// compile with: /clr /c  
ref struct C {  
   virtual void f();  
};  
  
ref struct D : C {  
   virtual int f() override ;   // C2553   
  
   // try the following line instead  
   // virtual void f() override;  
};  
```