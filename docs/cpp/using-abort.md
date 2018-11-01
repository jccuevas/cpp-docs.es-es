---
title: Usar abort
ms.date: 11/04/2016
f1_keywords:
- Abort
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: 0961f6f88f5de4d435fa65e50b9dbdbc478e7608
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591833"
---
# <a name="using-abort"></a>Usar abort

Una llamada a la [anular](../c-runtime-library/reference/abort.md) función provoca la finalización inmediata. Omite el proceso de destrucción normal de los objetos estáticos globales inicializados. También omite cualquier procesamiento especial especificado mediante la función `atexit`.

## <a name="see-also"></a>Vea también

[Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)