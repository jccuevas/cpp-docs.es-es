---
title: fsetpos
ms.date: 11/04/2016
api_name:
- fsetpos
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fsetpos
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: f44ab1b35c9e598f82dbc0af96979476ee353541
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956515"
---
# <a name="fsetpos"></a>fsetpos

Establece el indicador de posición de secuencia.

## <a name="syntax"></a>Sintaxis

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>Parámetros

*stream*<br/>
Puntero a la estructura **FILE**.

*pos*<br/>
Almacenamiento del indicador de posición.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **fsetpos** devuelve 0. En caso de error, la función devuelve un valor distinto de cero y establece **errno** en una de las siguientes constantes de manifiesto (definidas en errno. H): **EBADF**, que significa que no se puede tener acceso al archivo o que el objeto al que apunta el *flujo* no es una estructura de archivos válida. o **EINVAL**, lo que significa que se pasó un valor no válido para la *secuencia* o el *PDV* . Si se pasa un parámetro no válido, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Comentarios

La función **fsetpos** establece el indicador de posición de archivo de la *secuencia* en el valor de *pos*, que se obtiene en una llamada anterior a **fgetpos** en la *secuencia*. La función borra el indicador de fin de archivo y deshace los efectos de [ungetc](ungetc-ungetwc.md) en la *secuencia*. Después de llamar a **fsetpos**, la siguiente operación en la *secuencia* puede ser de entrada o de salida.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [fgetpos](fgetpos.md).

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
