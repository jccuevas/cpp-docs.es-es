---
title: Error del compilador C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: fb4a0e6f3f6ec227b978ae0b7d3864b2134de986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406826"
---
# <a name="compiler-error-c2834"></a>Error del compilador C2834

'operator operator' debe calificar globalmente

El `new` y `delete` operadores están asociados a la clase donde residen. Resolución de ámbito no se puede usar para seleccionar una versión de `new` o `delete` de una clase diferente. Para implementar varias formas de la `new` o `delete` (operador), cree una versión del operador con parámetros formales adicionales.