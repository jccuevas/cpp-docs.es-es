---
title: Error de compilador Error C2726 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2726
dev_langs:
- C++
helpviewer_keywords:
- C2726
ms.assetid: f0191bb7-c175-450b-bf09-a3213db96d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aaeab263c2deffe79de98be30808e2dca973ce56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236110"
---
# <a name="compiler-error-c2726"></a>Error C2726 de Error del compilador
'gcnew' solo se puede usar para crear un objeto con tipo WinRT o administrado  
  
 No se puede crear una instancia de un tipo nativo en el montón de recolección de elementos no utilizados.  
  
 En el ejemplo siguiente se genera el error C2726 y se muestra cómo corregirlo:  
  
```  
// C2726.cpp  
// compile with: /clr  
using namespace System;  
class U {};  
ref class V {};  
value class W {};  
  
int main() {  
   U* pU = gcnew U;    // C2726  
   U* pU2 = new U;   // OK  
   V^ p2 = gcnew V;   // OK  
   W p3;   // OK  
  
}  
```  
