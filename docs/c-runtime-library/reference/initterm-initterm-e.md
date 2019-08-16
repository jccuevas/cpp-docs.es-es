---
title: _initterm, _initterm_e
ms.date: 11/04/2016
apiname:
- _initterm_e
- _initterm
apilocation:
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _initterm_e
- initterm
- _initterm
- initterm_e
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
ms.openlocfilehash: 65963e95507d4d6444ebcc9038b5b8cf797f9feb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331667"
---
# <a name="initterm-initterme"></a>_initterm, _initterm_e

Métodos internos que recorren una tabla de punteros de función y los inicializan.

El primer puntero es la ubicación inicial de la tabla y el segundo puntero, la ubicación final.

## <a name="syntax"></a>Sintaxis

```C
void __cdecl _initterm(
   PVFV *,
   PVFV *
);

int __cdecl _initterm_e(
   PVFV *,
   PVFV *
);
```

## <a name="return-value"></a>Valor devuelto

Un código de error distinto de cero si se produce un error de inicialización y genera un error; 0 si no se produce ningún error.

## <a name="remarks"></a>Comentarios

Estos métodos solo se llaman internamente durante la inicialización de un programa de C++. No llame a estos métodos en un programa.

Cuando estos métodos recorren una tabla de entradas de función, omiten **NULL** entradas y continuar.

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
