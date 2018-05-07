---
title: Compilador advertencia (nivel 3) C4023 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4023
dev_langs:
- C++
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 213d72e39575b447787c3e0ead7910baedc8e815
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4023"></a>Advertencia del compilador (nivel 3) C4023
'símbolo': el puntero con base se pasó a la función sin prototipo: número de parámetro  
  
 Si se pasa un puntero con base a una función sin prototipo, el puntero se normaliza, con resultados imprevisibles.  
  
 Para resolver esta advertencia, use funciones prototipo a las que se pasan punteros con base.