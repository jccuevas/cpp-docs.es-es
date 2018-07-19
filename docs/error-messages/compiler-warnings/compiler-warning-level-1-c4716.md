---
title: Compilador advertencia (nivel 1) C4716 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4716
dev_langs:
- C++
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be620264c315fc9c2ff3cd4cb91bd9d77c8a4d07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288858"
---
# <a name="compiler-warning-level-1-c4716"></a>Advertencia del compilador (nivel 1) C4716
'function': la función debe devolver un valor  
  
 La función especificada no devolvió un valor.  
  
 Sólo funciona con un tipo de valor devuelto de void pueden usa el comando return sin un valor devuelto correspondiente.  
  
 Cuando se llama a esta función, se devolverá un valor indefinido.  
  
 Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, utilice [#pragma warning](../../preprocessor/warning.md).  
  
 El ejemplo siguiente genera C4716:  
  
```  
// C4716.cpp  
// compile with: /c /W1  
// C4716 expected  
#pragma warning(default:4716)  
int test() {  
   // uncomment the following line to resolve  
   // return 0;  
}  
```