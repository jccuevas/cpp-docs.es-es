---
title: Compilador advertencia (nivel 4) C4289 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4289
dev_langs: C++
helpviewer_keywords: C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 98acda62a984f2625ddc742e309aca7628d9c9f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4289"></a>Advertencia del compilador (nivel 4) C4289
se ha utilizado una extensión no estándar : 'var' : la variable de control de bucles declarada en el bucle For se utiliza fuera del ámbito del bucle For  
  
 Cuando se compila con [/Ze](../../build/reference/za-ze-disable-language-extensions.md) y **/Zc:forScope-**, una variable declarada en un [para](../../cpp/for-statement-cpp.md) bucle se usa después de la **para**-ámbito del bucle.  
  
 Vea [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) para obtener información acerca de cómo especificar el comportamiento estándar en **para** bucles con **/Ze**.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
 El ejemplo siguiente genera C4289:  
  
```  
// C4289.cpp  
// compile with: /W4 /Zc:forScope-  
#pragma warning(default:4289)  
int main() {  
   for (int i = 0 ; ; )   // C4289  
      break;  
   i++;  
}  
```