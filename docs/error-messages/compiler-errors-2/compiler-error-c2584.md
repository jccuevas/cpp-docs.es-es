---
title: Error del compilador C2584 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2584
dev_langs:
- C++
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae9ea7a4b0ce44231925f4231c5876f352765ad6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231078"
---
# <a name="compiler-error-c2584"></a>Error del compilador C2584
'Class': directa 'Base2' base es inaccesible; ya existe una base de 'Base1'  
  
 `Class` ya se deriva directamente de `Base1`. `Base2` También se deriva de `Base1`. `Class` no se puede derivar de `Base2` ya que eso significaría heredar (indirectamente) `Base1` nuevo, que no es válido porque `Base1` ya es una clase base directa.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2584.  
  
```  
// C2584.cpp  
// compile with: /c  
struct A1 {  
   virtual int MyFunction();  
};  
  
struct A2 {  
    virtual int MyFunction();  
};  
  
struct B1: public virtual A1, virtual A2 {  
    virtual int MyFunction();  
};  
  
struct B2: public virtual A2, virtual A1 {  
    virtual int MyFunction();  
};  
  
struct C: virtual B1, B2 {  
    virtual int MyFunction();  
};  
  
struct Z : virtual B2, virtual C {   // C2584  
// try the following line insted  
// struct Z : virtual C {  
    virtual int MyFunction();  
};  
```