---
title: Compilador advertencia (nivel 1) C4627 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4627
dev_langs: C++
helpviewer_keywords: C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 66d199b8dede21f94a963113341eb6426f66a807
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4627"></a>Advertencia del compilador (nivel 1) C4627
'\<identificador >': omite al buscar el precompilado uso del encabezado  
  
 Al buscar la ubicación donde se utiliza un encabezado precompilado, el compilador encontró una `#include` la directiva para la  *\<identificador >* archivo de inclusión. El compilador omite la `#include` directiva, pero emite la advertencia **C4627** si el encabezado precompilado aún no contiene el  *\<identificador >* archivo de inclusión.  
  
## <a name="see-also"></a>Vea también  
 [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)