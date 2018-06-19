---
title: Error del compilador C3364 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3364
dev_langs:
- C++
helpviewer_keywords:
- C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 337bcf71e89dc1ff3e434eba6645f76df1022a11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257852"
---
# <a name="compiler-error-c3364"></a>Error del compilador C3364
'delegado': constructor delegado: el argumento debe ser el puntero a función miembro de clase administrada o una función global  
  
 El segundo parámetro del constructor del delegado toma la dirección de una función miembro o la dirección de una función miembro estática de cualquier clase. Ambos se tratan como direcciones simples.  
  
 El ejemplo siguiente genera C3364:  
  
```  
// C3364_2.cpp  
// compile with: /clr  
  
delegate int D( int, int );  
  
ref class C {  
public:  
   int mf( int, int ) {  
      return 1;  
   }  
};  
  
int main() {  
   C^ pC = gcnew C;  
   System::Delegate^ pD = gcnew D( pC,pC->mf( 1, 2 ) ); // C3364  
  
   // try the following line instead  
   // System::Delegate^ pD = gcnew D(pC, &C::mf);  
}  
```  
