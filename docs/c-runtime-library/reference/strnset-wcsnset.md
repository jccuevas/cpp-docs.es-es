---
title: strnset, wcsnset
ms.date: 12/16/2019
api_name:
- strnset
- wcsnset
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
- wcsnset
- strnset
helpviewer_keywords:
- strnset function
- wcsnset function
ms.assetid: e7868ac9-dc34-4606-bd3c-0fb2e7c51631
ms.openlocfilehash: c1f00410dc15a329d6381af893eab44bb938f248
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301098"
---
# <a name="strnset-wcsnset"></a>strnset, wcsnset

Los nombres de función específicos de Microsoft `strnset` y `wcsnset` son alias desusados para las funciones [_strnset y _wcsnset](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md) . De forma predeterminada, generan la [Advertencia del compilador (nivel 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Los nombres están desusados porque no siguen las reglas estándar de C para los nombres específicos de la implementación. Sin embargo, las funciones todavía se admiten.

En su lugar, se recomienda usar [_strnset y _wcsnset](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md) o las funciones [_strnset_s y _wcsnset_s](strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md) con seguridad mejorada. O bien, puede seguir usando estos nombres de función y deshabilitar la advertencia. Para obtener más información, vea [desactivar la advertencia](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) y [los nombres de las funciones POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
