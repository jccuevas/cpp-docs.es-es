---
title: creat
ms.date: 12/16/2019
api_name:
- creat
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
- creat
helpviewer_keywords:
- creat function
ms.assetid: 3aa6f0cc-5ae6-40d5-be94-0ab6f53c0c5b
ms.openlocfilehash: 49a11b8a5edd0320ea3c2f46f9439ce621bcd4f9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299876"
---
# <a name="creat"></a>creat

El nombre de la función POSIX implementada por Microsoft `creat` es un alias en desuso para la función [_creat](creat-wcreat.md) . De forma predeterminada, genera una [Advertencia del compilador (nivel 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). El nombre está en desuso porque no sigue las reglas estándar de C para los nombres específicos de la implementación. Sin embargo, todavía se admite la función.

En su lugar, se recomienda usar [_creat](creat-wcreat.md) . O bien, puede seguir usando el nombre de esta función y deshabilitar la advertencia. Para obtener más información, vea [desactivar la advertencia](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) y [los nombres de las funciones POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
