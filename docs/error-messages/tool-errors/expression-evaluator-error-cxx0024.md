---
title: Error del evaluador de expresiones CXX0024 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0024
dev_langs:
- C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c96bd943719afb0d974a5c4386742bea24396fd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0024"></a>Error del evaluador de expresiones CXX0024
la operación necesita un valor l  
  
 Se especificó una expresión que no se evalúa como un valor l para una operación que requiere un valor l.  
  
 L-value (denominado así porque aparece en el lado izquierdo de una instrucción de asignación) es una expresión que hace referencia a una ubicación de memoria.  
  
 Por ejemplo, `buffer[count]` es un valor l válido porque señala a una ubicación de memoria específica. La comparación lógica `zed != 0` no es un valor l válido porque se evalúa como TRUE o FALSE, no como una dirección de memoria.  
  
 Este error es idéntico a CAN0024.