---
title: unlink
ms.date: 12/16/2019
api_name:
- unlink
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- unlink
helpviewer_keywords:
- unlink function
ms.assetid: 2cd82055-5770-48be-88ee-4b2c70541c46
ms.openlocfilehash: 5d8251c77a3c4d16ec6328c1c8e6d73d935db139
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301046"
---
# <a name="unlink"></a>unlink

El nombre de la función POSIX implementada por Microsoft `unlink` es un alias en desuso para la función [_unlink](unlink-wunlink.md) . De forma predeterminada, genera una [Advertencia del compilador (nivel 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). El nombre está en desuso porque no sigue las reglas estándar de C para los nombres específicos de la implementación. Sin embargo, todavía se admite la función.

En su lugar, se recomienda usar [_unlink](unlink-wunlink.md) . O bien, puede seguir usando el nombre de esta función y deshabilitar la advertencia. Para obtener más información, vea [desactivar la advertencia](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) y [los nombres de las funciones POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
