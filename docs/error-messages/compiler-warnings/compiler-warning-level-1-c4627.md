---
title: Compilador advertencia (nivel 1) C4627 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcde9e6707465fd95dbcb10e073a852624f0de0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284191"
---
# <a name="compiler-warning-level-1-c4627"></a>Advertencia del compilador (nivel 1) C4627
'\<identificador >': omite al buscar el precompilado uso del encabezado  
  
 Al buscar la ubicación donde se utiliza un encabezado precompilado, el compilador encontró una `#include` la directiva para la  *\<identificador >* archivo de inclusión. El compilador omite la `#include` directiva, pero emite la advertencia **C4627** si el encabezado precompilado aún no contiene el  *\<identificador >* archivo de inclusión.  
  
## <a name="see-also"></a>Vea también  
 [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)