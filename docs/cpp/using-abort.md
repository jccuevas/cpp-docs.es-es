---
title: Usar abort
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: e8cc7bce552acf67c0f9bf2025e0040dc051cff6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446419"
---
# <a name="using-abort"></a>Usar abort

La llamada a la función [Abort](../c-runtime-library/reference/abort.md) provoca una finalización inmediata. Omite el proceso de destrucción normal de los objetos estáticos globales inicializados. También omite cualquier procesamiento especial especificado mediante la función `atexit`.

## <a name="see-also"></a>Consulte también

[Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)