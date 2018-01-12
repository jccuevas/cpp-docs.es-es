---
title: Compilador advertencia (nivel 2) C4653 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4653
dev_langs: C++
helpviewer_keywords: C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8eb855e1c11136cd88c1c1e796d9759581e3ceb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4653"></a>Advertencia del compilador (nivel 2) C4653
opción del compilador 'opción' no es coherente con el encabezado precompilado; omitidas la opción de línea de comandos actual  
  
 Una opción especificada con utilizar encabezado precompilado ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) era incoherente con las opciones especificadas cuando se creó el encabezado precompilado. Esta compilación utilizó la opción especificada cuando se creó el encabezado precompilado.  
  
 Esta advertencia puede producirse cuando un valor diferente para la opción Empaquetar estructuras ([/Zp](../../build/reference/zp-struct-member-alignment.md)) se especificó durante la compilación del encabezado precompilado.