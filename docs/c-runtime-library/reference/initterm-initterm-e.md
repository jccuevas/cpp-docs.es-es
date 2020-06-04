---
title: _initterm, _initterm_e
ms.date: 11/04/2016
api_name:
- _initterm_e
- _initterm
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 7e85494bf6c8215d03602ee112e1ff2c0f1cf6f2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954618"
---
# <a name="_initterm-_initterm_e"></a>_initterm, _initterm_e

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

Cuando estos métodos recorren una tabla de entradas de función, omiten las entradas **nulas** y continúan.

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
