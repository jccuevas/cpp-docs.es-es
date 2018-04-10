---
title: Error del compilador C2834 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C2834
dev_langs:
- C++
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 616bb6fe351c7575bf04f319390d0a3cfcd3cc8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2834"></a>Error del compilador C2834
'operador' se debe calificar globalmente  
  
 El `new` y `delete` operadores están asociados a la clase donde residen. Resolución de ámbito no se puede usar para seleccionar una versión de `new` o `delete` de una clase diferente. Para implementar varias formas de la `new` o `delete` (operador), cree una versión del operador con parámetros formales adicionales.