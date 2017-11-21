---
title: Compilador advertencia (nivel 1) C4420 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4420
dev_langs: C++
helpviewer_keywords: C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 646e87243e6901827fb2d36076a95e6bcb63c3ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4420"></a>Advertencia del compilador (nivel 1) C4420
'operador': operador no disponible, se utiliza 'operador' en su lugar; comprobación en tiempo de ejecución puede suponer un riesgo  
  
 Esta advertencia se genera cuando se utiliza el [opción /RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector comprobación new/delete) y cuando no se encuentra ningún formulario de vector. En este caso, el formulario de vector no se utiliza.  
  
 A fin de opción /RTCv funcione correctamente, el compilador siempre debe llamar a la forma vectorial de [nueva](../../cpp/new-operator-cpp.md)/[eliminar](../../cpp/delete-operator-cpp.md) si se utiliza la sintaxis de vector.