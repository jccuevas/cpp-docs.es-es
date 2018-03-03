---
title: Error de compilador Error C2675 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2675
dev_langs:
- C++
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60bc86f87f6b1bd247d8f866b9d8bc7131f4898e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2675"></a>Error de C2675 de Error de compilador
'operador' unario: 'tipo' no define este operador o una conversión a un tipo aceptable para el operador predefinido  
  
 Error C2675 también puede producirse al usar un operador unario y el tipo no define el operador o una conversión a un tipo aceptable para el operador predefinido. Para usar este operador, debe sobrecargarlo para el tipo especificado o definir una conversión a un tipo para el que esté definido el operador.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C2675.  
  
```  
// C2675.cpp  
struct C {   
   C(){}  
} c;  
  
struct D {   
   D(){}  
   void operator-(){}  
} d;  
  
int main() {  
   -c;   // C2675  
   -d;   // OK  
}  
```