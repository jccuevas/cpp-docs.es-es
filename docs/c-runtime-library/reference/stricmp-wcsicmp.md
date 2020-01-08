---
title: stricmp, wcsicmp
ms.date: 12/16/2019
api_name:
- stricmp
- wcsicmp
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
- stricmp
- wcsicmp
helpviewer_keywords:
- stricmp function
- wcsicmp function
ms.assetid: 2e3c6703-2635-4961-a253-e2c4c5029ed8
ms.openlocfilehash: d47249a3b41c76bf87ece8ed2e8a0fbbfc05ff09
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300513"
---
# <a name="stricmp-wcsicmp"></a>stricmp, wcsicmp

Los nombres de función específicos de Microsoft `stricmp` y `wcsicmp` son alias desusados para las funciones [_stricmp y _wcsicmp](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md) . De forma predeterminada, generan la [Advertencia del compilador (nivel 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Los nombres están desusados porque no siguen las reglas estándar de C para los nombres específicos de la implementación. Sin embargo, las funciones todavía se admiten.

En su lugar, se recomienda usar [_stricmp o _wcsicmp](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md) . O bien, puede seguir usando estos nombres de función y deshabilitar la advertencia. Para obtener más información, vea [desactivar la advertencia](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) y [los nombres de las funciones POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
