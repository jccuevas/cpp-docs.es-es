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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 2ee68506437cb1c5b76cac05d674527095055055
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920411"
---
# <a name="_get_terminate"></a>_get_terminate

Devuelve la rutina de finalización a la que debe llamar **Terminate**.

## <a name="syntax"></a>Sintaxis

```C
terminate_function _get_terminate( void );
```

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función registrada por [set_terminate](set-terminate-crt.md). Si no se ha establecido ninguna función, el valor devuelto se puede utilizar para restaurar el comportamiento predeterminado; Este valor puede ser **null**.

## <a name="remarks"></a>Observaciones

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_terminate**|\<eh.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[aborta](abort.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[cancela](terminate-crt.md)<br/>
[esperado](unexpected-crt.md)<br/>
