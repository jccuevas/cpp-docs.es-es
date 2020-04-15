---
title: _get_terminate
ms.date: 4/2/2020
api_name:
- _get_terminate
- _o__get_terminate
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_terminate
- _get_terminate
- __get_terminate
helpviewer_keywords:
- __get_terminate function
- get_terminate function
- _get_terminate function
ms.assetid: c8f168c4-0ad5-4832-a522-dd1ef383c208
ms.openlocfilehash: fff90037851b23f3525f514aba0f6f913f9dd776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344934"
---
# <a name="_get_terminate"></a>_get_terminate

Devuelve la rutina de terminación a la que se llamará por **terminate**.

## <a name="syntax"></a>Sintaxis

```C
terminate_function _get_terminate( void );
```

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función registrada por [set_terminate](set-terminate-crt.md). Si no se ha establecido ninguna función, el valor devuelto se puede utilizar para restaurar el comportamiento predeterminado; este valor puede ser **NULL**.

## <a name="remarks"></a>Observaciones

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_terminate**|\<eh.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[Aborta](abort.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Terminar](terminate-crt.md)<br/>
[Inesperado](unexpected-crt.md)<br/>
