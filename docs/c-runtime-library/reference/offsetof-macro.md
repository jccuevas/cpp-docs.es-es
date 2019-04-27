---
title: offsetof (Macro)
ms.date: 11/04/2016
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
apitype: DLLExport
f1_keywords:
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: a0f367dbe6fa2681a7d413304f32b5699b8f7cee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156078"
---
# <a name="offsetof-macro"></a>offsetof (Macro)

Recupera el desplazamiento de un miembro desde el principio de su estructura primaria.

## <a name="syntax"></a>Sintaxis

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>Parámetros

*structName*<br/>
Nombre de la estructura de datos primaria.

*memberName*<br/>
Nombre del miembro de la estructura de datos primaria cuyo desplazamiento se determina.

## <a name="return-value"></a>Valor devuelto

**offsetof** devuelve el desplazamiento en bytes del miembro especificado desde el principio de su estructura de datos principal. No se define para campos de bits.

## <a name="remarks"></a>Comentarios

El **offsetof** macro devuelve el desplazamiento en bytes de *memberName* desde el principio de la estructura especificada por *structName* como un valor de tipo **size_ t**. Puede especificar tipos con el **struct** palabra clave.

> [!NOTE]
> **offsetof** no es una función y no se puede describir mediante un prototipo de C.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
