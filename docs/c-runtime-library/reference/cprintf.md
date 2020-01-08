---
title: cprintf
ms.date: 12/16/2019
api_name:
- cprintf
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
- cprintf
helpviewer_keywords:
- cprintf function
ms.assetid: 573e6634-d7e5-4856-8c01-627dcfbd5fc8
ms.openlocfilehash: 1f61043b1cf59ad31107bcfc333338a7493767cf
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299902"
---
# <a name="cprintf"></a>cprintf

El nombre de la función específica de Microsoft `cprintf` es un alias en desuso para la función [_cprintf](cprintf-cprintf-l-cwprintf-cwprintf-l.md) . De forma predeterminada, genera una [Advertencia del compilador (nivel 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). El nombre está en desuso porque no sigue las reglas estándar de C para los nombres específicos de la implementación. Sin embargo, todavía se admite la función.

En su lugar, se recomienda usar la función de [_cprintf_s](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md) [_cprintf](cprintf-cprintf-l-cwprintf-cwprintf-l.md) o con seguridad mejorada. O bien, puede seguir usando el nombre de esta función y deshabilitar la advertencia. Para obtener más información, vea [desactivar la advertencia](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) y [los nombres de las funciones POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).
