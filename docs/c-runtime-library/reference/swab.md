---
title: _swab
ms.date: 11/04/2016
apiname:
- _swab
- stdlib/_swab
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: 64753383bcb94947e6b413b5f55ac6e2d9c7dbca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603039"
---
# <a name="swab"></a>_swab

Intercambia los bytes.

## <a name="syntax"></a>Sintaxis

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>Parámetros

*src*<br/>
Datos que se van a copiar e intercambiar.

*dest*<br/>
Ubicación de almacenamiento de los datos intercambiados.

*n*<br/>
Número de bytes que se van a copiar e intercambiar.

## <a name="return-value"></a>Valor devuelto

El **swab** función no devuelve un valor. La función establece **errno** a **EINVAL** si el *src* o *dest* puntero es null o *n* es menor a cero y los parámetros no válidos se invoca el controlador, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.

## <a name="remarks"></a>Comentarios

Si *n* es par, el **_swab** función copias *n* bytes a partir de *src*, intercambia cada par de bytes contiguos y almacena el resultado en *dest*. Si *n* es impar, **_swab** copia e intercambia los primeros *n*-1 bytes de *src*, y no se copia el byte final. El **_swab** función normalmente se utiliza para preparar los datos binarios para transferirlos a un equipo que usa un orden de bytes diferente.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_swab**|C: \<stdlib.h> C++: \<cstdlib> o \<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>Vea también

[Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)<br/>
