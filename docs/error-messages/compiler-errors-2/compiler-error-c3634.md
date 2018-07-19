---
title: Error del compilador C3634 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3634
dev_langs:
- C++
helpviewer_keywords:
- C3634
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc7b30f01923ec4757ad1254f6646bc374d3f1da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263790"
---
# <a name="compiler-error-c3634"></a>Error del compilador C3634
'función': no se puede definir un método abstracto de un administrado o WinRTclass  
  
 Un método abstracto se puede declarar en una clase WinRT o administrada, pero no definirse.  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera el error C3634.  
  
```  
// C3634.cpp  
// compile with: /clr  
ref class C {  
   virtual void f() = 0;  
};  
  
void C::f() {   // C3634 - don't define managed class' pure virtual method  
}  
```  
