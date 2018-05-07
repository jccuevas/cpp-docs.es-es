---
title: Error del compilador C2834 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2834
dev_langs:
- C++
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eb4fb992f9213c4a4b456f786fd8f81308cec12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2834"></a>Error del compilador C2834
'operador' se debe calificar globalmente  
  
 El `new` y `delete` operadores están asociados a la clase donde residen. Resolución de ámbito no se puede usar para seleccionar una versión de `new` o `delete` de una clase diferente. Para implementar varias formas de la `new` o `delete` (operador), cree una versión del operador con parámetros formales adicionales.