---
title: __setusermatherr
ms.date: 11/04/2016
apiname:
- __setusermatherr
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __setusermatherr
helpviewer_keywords:
- __setusermatherr
ms.assetid: f306818d-381a-4d68-8739-71b92bacb5ea
ms.openlocfilehash: 116abd203cc289c63535a8e41a005a6fd248b08b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640471"
---
# <a name="setusermatherr"></a>__setusermatherr

Especifica una rutina proporcionada por el usuario para controlar los errores matemáticos, en lugar de la rutina [_matherr](../c-runtime-library/reference/matherr.md).

## <a name="syntax"></a>Sintaxis

```cpp
void __setusermatherr(
   _HANDLE_MATH_ERROR pf
   )
```

#### <a name="parameters"></a>Parámetros

*pf*<br/>
Puntero a una implementación de `_matherr` proporcionada por el usuario.

El tipo del parámetro *pf* se declara como `typedef int (__cdecl * _HANDLE_MATH_ERROR)(struct _exception *)`.

## <a name="remarks"></a>Comentarios

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__setusermatherr|matherr.c|