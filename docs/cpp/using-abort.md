---
title: Usar abort
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: db0f6cdcdaf4bca1b74d89a9415c4f7951455d80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187862"
---
# <a name="using-abort"></a>Usar abort

La llamada a la función [Abort](../c-runtime-library/reference/abort.md) provoca una finalización inmediata. Omite el proceso de destrucción normal de los objetos estáticos globales inicializados. También omite cualquier procesamiento especial especificado mediante la función `atexit`.

## <a name="see-also"></a>Consulte también

[Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)
