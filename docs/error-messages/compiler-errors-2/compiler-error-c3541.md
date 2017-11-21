---
title: Error del compilador C3541 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3541
dev_langs: C++
helpviewer_keywords: C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 78b4c228999560807aa28dbaecfaa8f0af7b379a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3541"></a>Error del compilador C3541
'type': typeid no se puede aplicar a un tipo que contiene 'auto'  
  
 El [typeid](../../windows/typeid-cpp-component-extensions.md) operador no se puede aplicar al tipo indicado porque contiene el `auto` especificador.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera C3541.  
  
```  
// C3541.cpp  
// Compile with /Zc:auto  
#include <typeinfo>  
int main() {  
    auto x = 123;  
    typeid(x);    // OK  
    typeid(auto); // C3541  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../../cpp/auto-keyword.md)   
 [/ Zc: Auto (deducir tipo de Variable)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [typeid](../../windows/typeid-cpp-component-extensions.md)