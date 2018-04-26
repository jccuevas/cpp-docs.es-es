---
title: _query_new_handler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _query_new_handler
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _query_new_handler
- query_new_handler
dev_langs:
- C++
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c59b12c57af4d8a3d40b1ced2ffdc2a2cb00bc1f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="querynewhandler"></a>_query_new_handler

Devuelve la dirección de la nueva rutina de controlador actual.

## <a name="syntax"></a>Sintaxis

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>Valor devuelto

Devuelve la dirección de la rutina del controlador nuevo actual según lo establecido por **_set_new_handler**.

## <a name="remarks"></a>Comentarios

C++ **_query_new_handler** función devuelve la dirección de la función de control de excepciones actual definida por el C++ [_set_new_handler](set-new-handler.md) (función). **_set_new_handler** se utiliza para especificar una función de control de excepciones que va a obtener el control si el **nueva** operador no puede asignar memoria. Para obtener más información, vea la descripción de los [operadores new y delete](../../cpp/new-and-delete-operators.md) en la referencia del lenguaje de C++.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
