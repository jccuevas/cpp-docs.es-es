---
title: Error del compilador C3873 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bec37b8fb00aedd83d91f1d001d77c42679ec038
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269440"
---
# <a name="compiler-error-c3873"></a>Error del compilador C3873
'char': este carácter no se permite como primer carácter de un identificador  
  
 El compilador de C++ respeta el estándar de C++11 respecto de los caracteres permitidos en un identificador. Solo se permiten determinados rangos de caracteres y nombres de carácter universal en un identificador. Se aplican restricciones adicionales respecto del carácter inicial de un identificador. Para obtener más información y una lista de caracteres permitidos y rangos de nombre de carácter universal, consulte [Identifiers](../../cpp/identifiers-cpp.md).  
  
 El rango de caracteres permitidos en un identificador es menos restrictivo cuando se compila código C++/CLI. Los identificadores del código compilado con /clr deben regirse por el  [Estándar ECMA-335: Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 En el siguiente ejemplo se genera el error C3873:  
  
```  
// C3873.cpp  
int main() {  
   int \u036F_abc;   // C3873, not in allowed range for initial character  
   int abc_\u036F;   // OK, in allowed range for non-initial character  
}  
```