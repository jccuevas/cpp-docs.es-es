---
title: Error del compilador C2524 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2524
dev_langs:
- C++
helpviewer_keywords:
- C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b21a907de69291c6d7fbc23f3ea093271a1ad3b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230074"
---
# <a name="compiler-error-c2524"></a>Error del compilador C2524
'destructor': un destructor/finalizador debe tener una lista de parámetros 'void'  
  
 El destructor o finalizador tiene una lista de parámetros que no es [void](../../cpp/void-cpp.md). No se permiten otros tipos de parámetros.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente reproduce el error C2524.  
  
```  
// C2524.cpp  
// compile with: /c  
class A {  
   A() {}  
   ~A(int i) {}    // C2524  
   // try the following line instead  
   // ~A() {}  
};  
```  
  
## <a name="example"></a>Ejemplo  
 El código siguiente reproduce el error C2524.  
  
```  
// C2524_b.cpp  
// compile with: /clr /c  
ref struct I1 {  
protected:  
   !I1(int i);   // C2524  
   // try the following line instead  
   // !I1();  
};  
```