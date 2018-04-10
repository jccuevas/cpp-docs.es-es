---
title: Error del compilador C2415 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C2415
dev_langs:
- C++
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ff0f423ec83b9951e806a2483417f3ab79f817a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2415"></a>Error del compilador C2415
tipo de operando incorrecto  
  
 El código de operación no utiliza los operandos de este tipo.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  El código de operación no admite el número de operandos utilizado. Revise el manual de referencia del lenguaje de ensamblado para determinar el número correcto de operandos.  
  
2.  Un procesador más reciente admite la instrucción con tipos adicionales. Ajustar la [/arch (arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md) opción para usar el procesador más reciente.