---
title: Error del compilador C2585 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2585
dev_langs:
- C++
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ab812a4b6621acb28a4df636056598047f5c21e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2585"></a>Error del compilador C2585
conversión explícita a 'tipo' es ambigua  
  
 La conversión de tipos puede producir más de un resultado.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Convertir de un tipo de clase o estructura basado en herencia múltiple. Si el tipo hereda la misma clase base más de una vez, la función de conversión o un operador debe utilizar la resolución de ámbito (`::`) para especificar cuál de las clases heredadas a usar en la conversión.  
  
2.  Se han definido un operador de conversión y un constructor que realiza la misma conversión.