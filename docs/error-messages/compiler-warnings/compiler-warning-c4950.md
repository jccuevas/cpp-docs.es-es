---
title: Advertencia del compilador C4950 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4950
dev_langs:
- C++
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0bad063bce3e99e64177476cea8470da0de81d3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4950"></a>Advertencia del compilador C4950
'type_or_member': marcado como obsoleto  
  
Un miembro o tipo se marcó como obsoleto con la <xref:System.ObsoleteAttribute> atributo.  
  
La advertencia C4950 siempre se emite como un error. Puede desactivar esta advertencia mediante la [advertencia](../../preprocessor/warning.md) directiva pragma o [/wd](../../build/reference/compiler-option-warning-level.md) opción del compilador.  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera la advertencia C4950:  
  
```cpp  
// C4950.cpp  
// compile with: /clr  
using namespace System;  
  
// Any reference to Func3 should generate an error with message  
[System::ObsoleteAttribute("Will be removed in next version", true)]  
Int32 Func3(Int32 a, Int32 b) {  
   return (a + b);  
}  
  
int main() {  
   Int32 MyInt3 = ::Func3(2, 2);   // C4950  
}  
```