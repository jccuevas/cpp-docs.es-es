---
title: j0, j1, jn
ms.date: 12/16/2019
api_name:
- jn
- j0
- j1
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
- jn
- j1
- j0
helpviewer_keywords:
- jn function
- j1 function
- j0 function
ms.assetid: ec8a9512-aacb-423c-a845-fc8927e6e21d
ms.openlocfilehash: a3dc02c1e85a57be119899a962d284d923cb42d8
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299239"
---
# <a name="j0-j1-jn"></a>j0, j1, jn

Los nombres de funciones POSIX implementadas por Microsoft `j0`, `j1`y `jn` son alias desusados para las funciones [_j0, _j1 y _jn](bessel-functions-j0-j1-jn-y0-y1-yn.md) . De forma predeterminada, generan la [Advertencia del compilador (nivel 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Los nombres están desusados porque no siguen las reglas estándar de C para los nombres específicos de la implementación. Sin embargo, las funciones todavía se admiten.

En su lugar, se recomienda usar [_j0, _j1 y _jn](bessel-functions-j0-j1-jn-y0-y1-yn.md) . O bien, puede seguir usando estos nombres de función y deshabilitar la advertencia. Para obtener más información, vea [desactivar la advertencia](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) y [los nombres de las funciones POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
