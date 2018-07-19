---
title: Compilador advertencia (nivel 4) C4960 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4960
dev_langs:
- C++
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1281bc86ad363c02df5c39ed41f616a6fff1a9b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294432"
---
# <a name="compiler-warning-level-4-c4960"></a>Advertencia del compilador (nivel 4) C4960
'function' es demasiado grande para generar un perfil  
  
 Al usar [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada con una función mayor que 65 535 instrucciones. Una función tan grande no está disponible para optimizaciones guiadas por perfil.  
  
 Para resolver esta advertencia, reduzca el tamaño de la función.