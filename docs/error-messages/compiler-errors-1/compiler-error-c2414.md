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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6238cf17686eb168a2f120c00fc34655715a950
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2414"></a>Error del compilador C2414
número de operandos no válido  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  El código de operación no admite el número de operandos utilizado. Revise el manual de referencia del lenguaje de ensamblado para determinar el número correcto de operandos.  
  
2.  Un procesador más reciente admite la instrucción con un número diferente de operandos. Ajustar la [/arch (arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md) opción para usar el procesador más reciente.