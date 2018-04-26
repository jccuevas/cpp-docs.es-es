---
title: fsetpos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fsetpos
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
- fsetpos
dev_langs:
- C++
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ceacacbe029488995c47e305682b56751347591
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

*Secuencia*<br/>
Puntero a la estructura **FILE**.

*punto de venta*<br/>
Almacenamiento del indicador de posición.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **fsetpos** devuelve 0. En caso de error, la función devuelve un valor distinto de cero y establece **errno** a uno de los siguientes (definidos en ERRNO de constantes del manifiesto. (H): **EBADF**, lo que significa que el archivo no está accesible o el objeto que *flujo* señala a no es una estructura de archivo válido; o **EINVAL**, lo que significa que un valor no válido para *flujo* o *pos* se pasó. Si se pasa un parámetro no válido, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Comentarios

El **fsetpos** función establece el indicador de posición de archivo para *flujo* en el valor de *pos*, que se obtiene en una llamada anterior a **fgetpos**contra *flujo*. La función borra el indicador de fin de archivo y deshace los efectos de [ungetc](ungetc-ungetwc.md) en *flujo*. Después de llamar a **fsetpos**, la siguiente operación en *flujo* puede ser de entrada o salida.

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
