---
title: Compilador advertencia (nivel 1) C4953 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0af5a16ebbf7851eceb2f2cd355f953b14c4bd38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4953"></a>Advertencia del compilador (nivel 1) C4953
La inclusión en líneas de 'function' se ha editado desde que los datos de perfil se recopilaron; datos de perfil no utilizados  
  
 Al usar [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada que se ha vuelto a compilar después de `/LTCG:PGINSTRUMENT` y tiene una función (***function***) que se editó y donde las ejecuciones de pruebas existentes identifican la función como candidata para la inclusión en líneas. Sin embargo, como resultado de volver a compilar el módulo, la función ya no será candidata para la inclusión en líneas.  
  
 Esta advertencia es informativa. Para resolver esta advertencia, ejecute `/LTCG:PGINSTRUMENT`, rehaga todas las pruebas y ejecute `/LTCG:PGOPTIMIZE`.  
  
 Esta advertencia se reemplazaría por un error si se hubiera usado `/LTCG:PGOPTIMIZE` .