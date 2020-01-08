---
title: cgets
ms.date: 12/16/2019
api_name:
- cgets
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
- cgets
helpviewer_keywords:
- cgets function
ms.assetid: 54faf257-5ed6-4301-be19-66d953e901fa
ms.openlocfilehash: 702bb75381eb458b3c98ac2991a28046ebb561a7
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299980"
---
# <a name="cgets"></a>cgets

El nombre de la función específica de Microsoft `cgets` es un alias en desuso para la función [_cgets](../cgets-cgetws.md) . De forma predeterminada, genera una [Advertencia del compilador (nivel 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). El nombre está en desuso porque no sigue las reglas estándar de C para los nombres específicos de la implementación. Sin embargo, todavía se admite la función.

En su lugar, se recomienda usar la función de [_cgets_s](cgets-s-cgetws-s.md) con seguridad mejorada. O bien, puede seguir usando el nombre de esta función y deshabilitar la advertencia. Para obtener más información, vea [desactivar la advertencia](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) y [los nombres de las funciones POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).
