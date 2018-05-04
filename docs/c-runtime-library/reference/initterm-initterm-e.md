---
title: _initterm, _initterm_e | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 470ad6cbf13efb170f61aa12f7859f2baa248c2b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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

Cuando estos métodos recorrer una tabla de entradas de la función, omiten **NULL** entradas y continuar.

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
