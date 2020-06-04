---
title: lsearch
ms.date: 12/16/2019
api_name:
- lsearch
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
- lsearch
helpviewer_keywords:
- lsearch function
ms.assetid: 130da3fc-904a-4375-b0ab-79bfea8a455f
ms.openlocfilehash: a068b6500de8a1a795f5494ac12afa0e5ca08544
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300890"
---
# <a name="lsearch"></a>lsearch

El nombre de la función POSIX implementada por Microsoft `lsearch` es un alias en desuso para la función [_lsearch](lsearch.md) . De forma predeterminada, genera una [Advertencia del compilador (nivel 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). El nombre está en desuso porque no sigue las reglas estándar de C para los nombres específicos de la implementación. Sin embargo, todavía se admite la función.

En su lugar, se recomienda usar [_lsearch](lsearch.md) o la función de [_lsearch_s](lsearch-s.md) con seguridad mejorada. O bien, puede seguir usando el nombre de esta función y deshabilitar la advertencia. Para obtener más información, vea [desactivar la advertencia](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) y [los nombres de las funciones POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
