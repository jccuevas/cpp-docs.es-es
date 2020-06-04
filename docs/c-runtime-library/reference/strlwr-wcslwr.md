---
title: strlwr, wcslwr
ms.date: 12/16/2019
api_name:
- strlwr
- wcslwr
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
- wcslwr
- strlwr
helpviewer_keywords:
- strlwr function
- wcslwr function
ms.assetid: b9274824-4365-4674-b656-823c89653656
ms.openlocfilehash: ff730d6bea6619c50fefb407a7a69c50e1a06af0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301085"
---
# <a name="strlwr-wcslwr"></a>strlwr, wcslwr

Los nombres de función específicos de Microsoft `strlwr` y `wcslwr` son alias desusados para las funciones [_strlwr y _wcslwr](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) . De forma predeterminada, generan la [Advertencia del compilador (nivel 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Los nombres están desusados porque no siguen las reglas estándar de C para los nombres específicos de la implementación. Sin embargo, las funciones todavía se admiten.

En su lugar, se recomienda usar [_strlwr o _wcslwr](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) o las funciones [_strlwr_s y _wcslwr_s](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md) con seguridad mejorada. O bien, puede seguir usando estos nombres de función y deshabilitar la advertencia. Para obtener más información, vea [desactivar la advertencia](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) y [los nombres de las funciones POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
