---
title: strdup, wcsdup
ms.date: 12/16/2019
api_name:
- wcsdup
- strdup
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
- wcsdup
- strdup
helpviewer_keywords:
- wcsdup function
- strdup function
ms.assetid: c9ac0935-b525-4e95-8a64-396fc7e34ee9
ms.openlocfilehash: e381a1933a6b657108a66053bad1c7ff795c1a29
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300526"
---
# <a name="strdup-wcsdup"></a>strdup, wcsdup

Los nombres de funciones POSIX implementadas por Microsoft `strdup` y `wcsdup` son alias desusados para las funciones [_strdup y _wcsdup](strdup-wcsdup-mbsdup.md) . De forma predeterminada, generan la [Advertencia del compilador (nivel 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Los nombres están desusados porque no siguen las reglas estándar de C para los nombres específicos de la implementación. Sin embargo, las funciones todavía se admiten.

En su lugar, se recomienda usar [_strdup y _wcsdup](strdup-wcsdup-mbsdup.md) . O bien, puede seguir usando estos nombres de función y deshabilitar la advertencia. Para obtener más información, vea [desactivar la advertencia](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) y [los nombres de las funciones POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
