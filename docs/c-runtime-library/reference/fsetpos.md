---
title: fsetpos
ms.date: 4/2/2020
api_name:
- fsetpos
- _o_fsetpos
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8fa6ec1f37703ce51e0c9c565d766c56cf164322
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910181"
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

*misiones*<br/>
Puntero a la estructura **FILE**.

*abre*<br/>
Almacenamiento del indicador de posición.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **fsetpos** devuelve 0. En caso de error, la función devuelve un valor distinto de cero y establece **errno** en una de las siguientes constantes de manifiesto (definidas en errno. H): **EBADF**, lo que significa que no se puede acceder al archivo o que el objeto al que apunta el *flujo* no es una estructura de archivos válida. o **EINVAL**, lo que significa que se pasó un valor no válido para la *secuencia* o el *PDV* . Si se pasa un parámetro no válido, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Observaciones

La función **fsetpos** establece el indicador de posición de archivo de la *secuencia* en el valor de *pos*, que se obtiene en una llamada anterior a **fgetpos** en la *secuencia*. La función borra el indicador de fin de archivo y deshace los efectos de [ungetc](ungetc-ungetwc.md) en la *secuencia*. Después de llamar a **fsetpos**, la siguiente operación en la *secuencia* puede ser de entrada o de salida.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [fgetpos](fgetpos.md).

## <a name="see-also"></a>Consulta también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
