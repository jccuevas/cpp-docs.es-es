---
title: _heapwalk | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _heapwalk
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
- heapwalk
- _heapwalk
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d98260ce281bc8773f597dae5897afe4beee0bc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403406"
---
# <a name="heapwalk"></a>_heapwalk

Recorre el montón y devuelve información sobre la entrada siguiente.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows Runtime, salvo en compilaciones Debug. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _heapwalk( _HEAPINFO *entryinfo );
```

### <a name="parameters"></a>Parámetros

*entryinfo*<br/>
Búfer que contendrá la información del montón.

## <a name="return-value"></a>Valor devuelto

**_heapwalk** devuelve una de las siguientes constantes de manifiesto enteras definidas en Malloc.h.

|Valor devuelto|Significado|
|-|-|
|**_HEAPBADBEGIN**| La información de encabezado inicial no es válida o no se encuentra.|
|**_HEAPBADNODE**| Se ha encontrado un montón dañado o un nodo incorrecto.|
|**_HEAPBADPTR**| El **_pentry** campo de la **_HEAPINFO** estructura no contiene un puntero válido en el montón o *entryinfo* es un puntero nulo.|
|**_HEAPEND**| Se ha llegado al final del montón correctamente.|
|**_HEAPEMPTY**| El montón no está inicializado.|
|**_HEAPOK**| Ningún error hasta el momento. *entryinfo* se actualiza con información acerca de la siguiente entrada del montón.|

Además, si se produce un error, **_heapwalk** establece **errno** a **ENOSYS**.

## <a name="remarks"></a>Comentarios

El **_heapwalk** función le ayuda a depurar problemas relacionados con el montón en programas. La función recorre el montón, atravesando una entrada por cada llamada y devuelve un puntero a una estructura de tipo **_HEAPINFO** que contiene información sobre la siguiente entrada del montón. El **_HEAPINFO** tipo, definida en Malloc.h, contiene los siguientes elementos.

|Campo|Significado|
|-|-|
|`int *_pentry`|Puntero de entrada en el montón.|
|`size_t _size`|Tamaño de la entrada del montón.|
|`int _useflag`|Marca que indica si la entrada del montón está en uso.|

Una llamada a **_heapwalk** que devuelve **_HEAPOK** almacena el tamaño de la entrada en el **_size** campo y establece el **_useflag** campo cualquiera **_FREEENTRY** o **_USEDENTRY** (ambos son constantes definidas en Malloc.h). Para obtener esta información acerca de la primera entrada en el montón, pase **_heapwalk** un puntero a un **_HEAPINFO** estructura cuyo **_pentry** miembro es **NULL** . Si el sistema operativo no admite **_heapwalk**(por ejemplo, Windows 98), la función devuelve **_HEAPEND** y establece **errno** a **ENOSYS**.

Esta función valida su parámetro. Si *entryinfo* es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **_HEAPBADPTR**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_heapwalk**|\<malloc.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_heapwalk.c

// This program "walks" the heap, starting
// at the beginning (_pentry = NULL). It prints out each
// heap entry's use, location, and size. It also prints
// out information about the overall state of the heap as
// soon as _heapwalk returns a value other than _HEAPOK
// or if the loop has iterated 100 times.

#include <stdio.h>
#include <malloc.h>

void heapdump(void);

int main(void)
{
    char *buffer;

    heapdump();
    if((buffer = (char *)malloc(59)) != NULL)
    {
        heapdump();
        free(buffer);
    }
    heapdump();
}

void heapdump(void)
{
    _HEAPINFO hinfo;
    int heapstatus;
    int numLoops;
    hinfo._pentry = NULL;
    numLoops = 0;
    while((heapstatus = _heapwalk(&hinfo)) == _HEAPOK &&
          numLoops < 100)
    {
        printf("%8s block at %Fp of size %4.4X\n",
               (hinfo._useflag == _USEDENTRY ? "USED" : "FREE"),
               hinfo._pentry, hinfo._size);
        numLoops++;
    }

    switch(heapstatus)
    {
    case _HEAPEMPTY:
        printf("OK - empty heap\n");
        break;
    case _HEAPEND:
        printf("OK - end of heap\n");
        break;
    case _HEAPBADPTR:
        printf("ERROR - bad pointer to heap\n");
        break;
    case _HEAPBADBEGIN:
        printf("ERROR - bad start of heap\n");
        break;
    case _HEAPBADNODE:
        printf("ERROR - bad node in heap\n");
        break;
    }
}
```

```Output
    USED block at 00310650 of size 0100
    USED block at 00310758 of size 0800
    USED block at 00310F60 of size 0080
    FREE block at 00310FF0 of size 0398
    USED block at 00311390 of size 000D
    USED block at 003113A8 of size 00B4
    USED block at 00311468 of size 0034
    USED block at 003114A8 of size 0039
...
    USED block at 00312228 of size 0010
    USED block at 00312240 of size 1000
    FREE block at 00313250 of size 1DB0
OK - end of heap
```

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapchk](heapchk.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
