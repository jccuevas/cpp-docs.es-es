---
title: Error del compilador C2414 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2414
dev_langs:
- C++
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f3b532fdb8448f616916adcaf047dc83923f62c0
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2414"></a>Error del compilador C2414
número de operandos no válido  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  El código de operación no admite el número de operandos utilizado. Revise el manual de referencia del lenguaje de ensamblado para determinar el número correcto de operandos.  
  
2.  Un procesador más reciente admite la instrucción con un número diferente de operandos. Ajustar la [/arch (arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md) opción para usar el procesador más reciente.
