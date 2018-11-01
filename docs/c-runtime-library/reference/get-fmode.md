---
title: _get_fmode
ms.date: 11/04/2016
apiname:
- _get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: f326069c1c190b0fa1c1bbd5ee4ead7346481a38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658034"
---
# <a name="getfmode"></a>_get_fmode

Obtiene el modo de traducción de archivos predeterminado para las operaciones de E/S de archivo.

## <a name="syntax"></a>Sintaxis

```C
errno_t _get_fmode( 
   int * pmode 
);
```

### <a name="parameters"></a>Parámetros

*pmode*<br/>
Un puntero a un entero que se va a rellenar con el modo predeterminado actual: **_O_TEXT** o **_O_BINARY**.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Si *pmode* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **EINVAL**.

## <a name="remarks"></a>Comentarios

La función obtiene el valor de la variable global [_fmode](../../c-runtime-library/fmode.md). Esta variable especifica el modo de traducción de archivos predeterminado para ambos bajo nivel y transmitir las operaciones de E/S de archivos, como **_open**, **_pipe**, **fopen**, y [ freopen](freopen-wfreopen.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_set_fmode](set-fmode.md).

## <a name="see-also"></a>Vea también

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
