---
title: Error del compilador C3612 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3612
dev_langs:
- C++
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e07c899dbacdc58e9048ffa21d6be1b6abc02632
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252850"
---
# <a name="compiler-error-c3612"></a>Error del compilador C3612
'type': una clase sellada no puede ser abstracta  
  
Tipos definidos mediante `value` son sealed de forma predeterminada, y una clase es abstracta, a menos que implementa todos los métodos de su base. Una clase abstracta sealed no puede ser una clase base ni se puede crear instancias.  
  
Para obtener más información, consulte [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera C3612:  
  
```  
// C3612.cpp  
// compile with: /clr /c  
value struct V: public System::ICloneable {};   // C3612  
  
// OK  
value struct V2: public System::ICloneable {  
   Object^ Clone();  
};  
```