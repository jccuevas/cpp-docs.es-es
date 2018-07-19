---
title: Error del compilador C3638 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3638
dev_langs:
- C++
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3edb1a05323187b4a5dfcc2356da4a1ff8b874de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267095"
---
# <a name="compiler-error-c3638"></a>Error del compilador C3638
'operador': no se puede redefinir la conversión boxing estándar y los operadores de conversión unboxing  
  
 El compilador define un operador de conversión para cada clase administrada para admitir la conversión boxing implícita. No se puede volver a definir este operador.  
  
 Para obtener más información, consulte [conversión Boxing implícita](../../windows/boxing-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera C3638:  
  
```  
// C3638.cpp  
// compile with: /clr  
value struct V {  
   V(){}  
   static operator V^(V);   // C3638  
};  
  
int main() {  
   V myV;  
   V ^ pmyV = myV;   // operator supports implicit boxing  
}  
```