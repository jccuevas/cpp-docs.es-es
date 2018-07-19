---
title: Compilador advertencia (nivel 1) C4420 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4420
dev_langs:
- C++
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98336a30e7174b62df48e93a04ba9ee7ddcc919a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279115"
---
# <a name="compiler-warning-level-1-c4420"></a>Advertencia del compilador (nivel 1) C4420
'operador': operador no disponible, se utiliza 'operador' en su lugar; comprobación en tiempo de ejecución puede suponer un riesgo  
  
 Esta advertencia se genera cuando se utiliza el [opción /RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector comprobación new/delete) y cuando no se encuentra ningún formulario de vector. En este caso, el formulario de vector no se utiliza.  
  
 A fin de opción /RTCv funcione correctamente, el compilador siempre debe llamar a la forma vectorial de [nueva](../../cpp/new-operator-cpp.md)/[eliminar](../../cpp/delete-operator-cpp.md) si se utiliza la sintaxis de vector.