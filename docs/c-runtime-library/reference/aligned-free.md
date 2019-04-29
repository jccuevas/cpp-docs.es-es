---
title: _aligned_free
ms.date: 11/04/2016
apiname:
- _aligned_free
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
- aligned_free
- _aligned_free
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
ms.openlocfilehash: e2d1dc1172d1cd0d31f8daa8125bd052252393c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341657"
---
# <a name="alignedfree"></a>_aligned_free

Libera un bloque de memoria que se ha asignado con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Sintaxis

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria que se devolvió a las funciones `_aligned_malloc` o `_aligned_offset_malloc`.

## <a name="remarks"></a>Comentarios

**_aligned_free** está marcado como `__declspec(noalias)`, lo que significa que se garantiza que la función no se puede modificar las variables globales. Para obtener más información, consulte [noalias](../../cpp/noalias.md).

Esta función no valida su parámetro, a diferencia de las demás funciones _aligned de CRT. Si *memblock* es un puntero nulo, esta función simplemente realiza ninguna acción. No modifica `errno` ni invoca al controlador de parámetros no válidos. Si se produce un error en la función debido a que no usa funciones _aligned previamente para asignar el bloque de memoria o se produce un error de alineación de memoria debido a algún desastre imprevisto, la función genera un informe de depuración de [_RPT, _RPTF, _RPTW, _RPTFW (Macros)](rpt-rptf-rptw-rptfw-macros.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>Ejemplo

Para obtener más información, consulte [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Vea también

[Alineación de datos](../../c-runtime-library/data-alignment.md)