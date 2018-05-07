---
title: Las herramientas del vinculador LNK1301 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1301
dev_langs:
- C++
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b4e298ad3815c741ff6c901ac39bf7838ed135d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1301"></a>Error de las herramientas del vinculador LNK1301
LTCG módulos clr encontrados, incompatibles con/LTCG: parámetro  
  
 Un módulo compilado con /clr y /GL se pasó al vinculador junto con una de las optimizaciones guiadas por perfiles parámetros (PGO) de/LTCG.  
  
 Optimizaciones guiadas por perfiles no se admiten para los módulos / CLR.  
  
 Para obtener más información, consulte:  
  
-   [/GL (Optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md)  
  
-   [/LTCG (Generación de código en tiempo de enlace)](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  No compile con /clr o no crear vínculo con uno de los parámetros PGO en/LTCG.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error LNK1301:  
  
```  
// LNK1301.cpp  
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj  
// LNK1301 expected  
class MyClass {  
public:  
   int i;  
};  
```