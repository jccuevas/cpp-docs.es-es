---
title: Error del compilador C3540 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3540
dev_langs:
- C++
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27bae73d387612be41d8462bf0e5e0d82516ba1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256049"
---
# <a name="compiler-error-c3540"></a>Error del compilador C3540
'type': no se puede aplicar sizeof a un tipo que contiene 'auto'  
  
 El [sizeof](../../cpp/sizeof-operator.md) operador no se puede aplicar al tipo indicado porque contiene el `auto` especificador.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3540.  
  
```  
// C3540.cpp  
// Compile with /Zc:auto  
int main() {  
    auto x = 123;  
    sizeof(x);    // OK  
    sizeof(auto); // C3540  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../../cpp/auto-keyword.md)   
 [/ Zc: Auto (deducir tipo de Variable)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof (operador)](../../cpp/sizeof-operator.md)