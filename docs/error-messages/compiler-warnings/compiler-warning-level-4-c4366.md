---
title: Compilador advertencia (nivel 4) C4366 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4366
dev_langs: C++
helpviewer_keywords: C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 221cc02e5a2592599bad0ee9a77de59b19dda6f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4366"></a>Advertencia del compilador (nivel 4) C4366
El resultado del operador 'operador' unario puede desalineado  
  
 Si un miembro de estructura alguna vez podría ser desalineado debido al empaquetado, el compilador generará una advertencia cuando que la dirección del miembro se asigna a un puntero alineado. De forma predeterminada, todos los punteros están alineados.  
  
 Para resolver C4366, cambiar la alineación de la estructura o declare el puntero con el [__unaligned](../../cpp/unaligned.md) palabra clave.  
  
 Para obtener más información, vea __unaligned y [pack](../../preprocessor/pack.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4366.  
  
```  
// C4366.cpp  
// compile with: /W4 /c  
// processor: IPF x64  
#pragma pack(1)  
struct X {  
   short s1;  
   int s2;  
};  
  
int main() {  
   X x;  
   short * ps1 = &x.s1;   // OK  
   int * ps2 = &x.s2;   // C4366  
}  
```