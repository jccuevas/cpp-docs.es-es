---
title: Compilador advertencia (nivel 1) C4964 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4964
dev_langs: C++
helpviewer_keywords: C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1c7483b82c363898bc16ed5fc7d48f9cf0b35c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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