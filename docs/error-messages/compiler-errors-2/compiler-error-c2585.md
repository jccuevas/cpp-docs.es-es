---
title: Error del compilador C2585 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2585
dev_langs:
- C++
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cb0720c7fa9cde9a735c4353bb6bf1d8714ff0fd
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2585"></a>Error del compilador C2585
conversión explícita a 'tipo' es ambigua  
  
 La conversión de tipos puede producir más de un resultado.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Convertir de un tipo de clase o estructura basado en herencia múltiple. Si el tipo hereda la misma clase base más de una vez, la función de conversión o un operador debe utilizar la resolución de ámbito (`::`) para especificar cuál de las clases heredadas a usar en la conversión.  
  
2.  Se han definido un operador de conversión y un constructor que realiza la misma conversión.
