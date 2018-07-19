---
title: Compilador advertencia (nivel 4) C4234 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4234
dev_langs:
- C++
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8d5b7a2999b77c0b34ee925f5dd85a0a27c63f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293522"
---
# <a name="compiler-warning-level-4-c4234"></a>Advertencia del compilador (nivel 4) C4234
ha utilizado una extensión no estándar: 'palabra clave' palabra clave reservado para uso futuro  
  
 El compilador aún no implementa la palabra clave utilizada.  
  
 Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, utilice [#pragma warning](../../preprocessor/warning.md). Por ejemplo, para convertir C4234 en una advertencia de nivel 4  
  
```  
#pragma warning(2:4234)  
```  
  
 en el archivo de código fuente.