---
title: Error del evaluador de expresiones CXX0024 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0024
dev_langs: C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 386e04d8aa1655896b77f8492d7929778edd6109
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0024"></a>Error del evaluador de expresiones CXX0024
la operación necesita un valor l  
  
 Se especificó una expresión que no se evalúa como un valor l para una operación que requiere un valor l.  
  
 L-value (denominado así porque aparece en el lado izquierdo de una instrucción de asignación) es una expresión que hace referencia a una ubicación de memoria.  
  
 Por ejemplo, `buffer[count]` es un valor l válido porque señala a una ubicación de memoria específica. La comparación lógica `zed != 0` no es un valor l válido porque se evalúa como TRUE o FALSE, no como una dirección de memoria.  
  
 Este error es idéntico a CAN0024.