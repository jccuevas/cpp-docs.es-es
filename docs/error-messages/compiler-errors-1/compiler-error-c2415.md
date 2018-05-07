---
title: Error del compilador C2415 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2415
dev_langs:
- C++
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ad06cdf891c9b958f6cf08e724f4003a8507c2d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2415"></a>Error del compilador C2415
tipo de operando incorrecto  
  
 El código de operación no utiliza los operandos de este tipo.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  El código de operación no admite el número de operandos utilizado. Revise el manual de referencia del lenguaje de ensamblado para determinar el número correcto de operandos.  
  
2.  Un procesador más reciente admite la instrucción con tipos adicionales. Ajustar la [/arch (arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md) opción para usar el procesador más reciente.