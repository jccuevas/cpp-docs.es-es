---
title: Compilador advertencia (nivel 4) C4514 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4514
dev_langs:
- C++
helpviewer_keywords:
- C4514
ms.assetid: cdae966a-9cd4-4e31-af30-2a014e68f614
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89b61155b42cf6ba9106c5079ebbf74d4050cf99
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294695"
---
# <a name="compiler-warning-level-4-c4514"></a>Advertencia del compilador (nivel 4) C4514
'función': se ha quitado la función inline no referenciada  
  
 El optimizador quitó una función insertada que no se llama.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
 El ejemplo siguiente genera C4514:  
  
```  
// C4514.cpp  
// compile with: /W4  
#pragma warning(default : 4514)  
class A  
{  
   public:  
      void func()   // C4514, remove the function to resolve  
      {  
      }  
};  
  
int main()  
{  
}  
```