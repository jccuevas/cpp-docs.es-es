---
title: _set_new_mode
ms.date: 4/2/2020
api_name:
- _set_new_mode
- _o__set_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: f3635d462d2c7438ce985d74ff347120c02c82e0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920100"
---
# <a name="_set_new_mode"></a>_set_new_mode

Establece un nuevo modo de controlador para **malloc**.

## <a name="syntax"></a>Sintaxis

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parámetros

*newhandlermode*<br/>
Nuevo modo de controlador para **malloc**; el valor válido es 0 o 1.

## <a name="return-value"></a>Valor devuelto

Devuelve el modo de controlador anterior establecido para **malloc**. Un valor devuelto de 1 indica que, en caso de error de asignación de memoria, **malloc** anteriormente llamó a la rutina del nuevo controlador. un valor devuelto de 0 indica que no lo hizo. Si el argumento *newhandlermode* no es igual a 0 o 1, devuelve-1.

## <a name="remarks"></a>Observaciones

La función **_set_new_mode** de C++ establece el nuevo modo de controlador para [malloc](malloc.md). El nuevo modo de controlador indica si, en caso de error, **malloc** es llamar a la rutina del nuevo controlador tal y como se establece en [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del nuevo controlador en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **malloc** no pueda asignar memoria, **malloc** llame a la rutina del nuevo controlador de la misma manera que el operador **New** cuando se produce un error por la misma razón. Para obtener más información, vea los operadores [new](../../cpp/new-operator-cpp.md) y [delete](../../cpp/delete-operator-cpp.md) en *Referencia de lenguaje C++*. Para invalidar el valor predeterminado, llame a:

```cpp
_set_new_mode(1);
```

temprano en el programa o vincular con newmode. obj (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)).

Esta función valida su parámetro. Si *newhandlermode* es distinto de 0 o 1, la función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, <strong>_set_new_mode</strong> devuelve-1 y establece **errno** en `EINVAL`.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[ningún](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
