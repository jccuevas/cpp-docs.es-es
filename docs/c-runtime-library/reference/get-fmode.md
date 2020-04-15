---
title: _get_fmode
ms.date: 4/2/2020
api_name:
- _get_fmode
- _o__get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: fbaa30d0842400037f37508df94726f3e7fd7090
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345166"
---
# <a name="_get_fmode"></a>_get_fmode

Obtiene el modo de traducción de archivos predeterminado para las operaciones de E/S de archivo.

## <a name="syntax"></a>Sintaxis

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>Parámetros

*pmode*<br/>
Puntero a un entero que se va a rellenar con el modo predeterminado actual: **_O_TEXT** o **_O_BINARY**.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Si *pmode* es **NULL**, se invoca el controlador de parámetros no válidos como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **EINVAL**.

## <a name="remarks"></a>Observaciones

La función obtiene el valor de la variable global [_fmode](../../c-runtime-library/fmode.md). Esta variable especifica el modo de traducción de archivos predeterminado para las operaciones de E/S de archivos de flujo y de bajo nivel, como **_open**, **_pipe**, **fopen**y [freopen](freopen-wfreopen.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_set_fmode](set-fmode.md).

## <a name="see-also"></a>Consulte también

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[Texto y E/S de archivos en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
