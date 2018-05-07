---
title: Compilador advertencia (nivel 1) C4964 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4964
dev_langs:
- C++
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98226b2da465d2301356939273d370d76edcb64e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4964"></a>Advertencia del compilador (nivel 1) C4964
No se especificaron opciones de optimización; no se recopilará la información de perfil  
  
 [/ GL](../../build/reference/gl-whole-program-optimization.md) y [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) se han especificado, pero no hay optimizaciones se solicitaron, por lo que no se generará ningún archivo .pgc y, por lo tanto, no será posibles optimizaciones guiadas por perfiles.  
  
 Si desea que los archivos .pgc generarse cuando se ejecuta la aplicación, especifique uno de los [/O](../../build/reference/o-options-optimize-code.md) opciones del compilador.  
  
 El ejemplo siguiente genera C4964:  
  
```  
// C4964.cpp  
// compile with: /W1 /GL /link /ltcg:pgi  
// C4964 expected  
// Add /O2, for example, to the command line to resolve this warning.  
int main() {  
   int i;  
}  
```