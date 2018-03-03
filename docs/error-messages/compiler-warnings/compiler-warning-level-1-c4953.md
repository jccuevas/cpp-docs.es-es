---
title: Compilador advertencia (nivel 1) C4953 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c330076e7c0b4ff6daded94ef5fc038bd9dad759
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4953"></a>Advertencia del compilador (nivel 1) C4953
La inclusión en líneas de 'function' se ha editado desde que los datos de perfil se recopilaron; datos de perfil no utilizados  
  
 Al usar [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada que se ha vuelto a compilar después de `/LTCG:PGINSTRUMENT` y tiene una función (***function***) que se editó y donde las ejecuciones de pruebas existentes identifican la función como candidata para la inclusión en líneas. Sin embargo, como resultado de volver a compilar el módulo, la función ya no será candidata para la inclusión en líneas.  
  
 Esta advertencia es informativa. Para resolver esta advertencia, ejecute `/LTCG:PGINSTRUMENT`, rehaga todas las pruebas y ejecute `/LTCG:PGOPTIMIZE`.  
  
 Esta advertencia se reemplazaría por un error si se hubiera usado `/LTCG:PGOPTIMIZE` .