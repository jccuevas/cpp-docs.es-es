---
title: Las herramientas del vinculador LNK4224 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4224
dev_langs:
- C++
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96399e0c66eb3cb719073b2318513cd680723d97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4224"></a>Advertencia de las herramientas del vinculador LNK4224
ya no se admite la opción; pasa por alto  
  
 Se especificó una opción del vinculador no válido, obsoleta y se omitió.  
  
 Por ejemplo, LNK4224 puede producirse si una directiva/comment aparece en. obj. La directiva/comment se habría agregado a través de la [comentario) (C/C ++)](../../preprocessor/comment-c-cpp.md) pragma, utilizando la opción exestr en desuso. Utilice dumpbin [/ALL](../../build/reference/all.md) para ver las directivas del vinculador en un archivo .obj.  
  
 Si es posible, modifique el origen para el archivo .obj y quite el pragma. Si pasar por alto esta advertencia, es posible que un .executable compilado con **/CLR: pure** no se ejecutará como se esperaba.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia LNK4224.  
  
```  
// LNK4224.cpp  
// compile with: /c /Zi  
// post-build command: link LNK4224.obj /debug /debugtype:map  
int main () {  
   return 0;  
}  
```