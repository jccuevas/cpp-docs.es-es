---
title: Error del compilador C2834 | Microsoft Docs
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
ms.openlocfilehash: b94e1a3fba9bc3589af020340651b4546347cf1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089351"
---
# <a name="compiler-error-c2834"></a>Error del compilador C2834

'operator operator' debe calificar globalmente

El `new` y `delete` operadores están asociados a la clase donde residen. Resolución de ámbito no se puede usar para seleccionar una versión de `new` o `delete` de una clase diferente. Para implementar varias formas de la `new` o `delete` (operador), cree una versión del operador con parámetros formales adicionales.