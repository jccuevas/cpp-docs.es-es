---
title: offsetof (Macro)
ms.date: 11/04/2016
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: 278fca89046fcfc98e8c3ff726918cb4319e4ab0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951255"
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

**PosiciónInicial** devuelve el desplazamiento en bytes del miembro especificado desde el principio de su estructura de datos primaria. No se define para campos de bits.

## <a name="remarks"></a>Comentarios

La macro **offsete** devuelve el desplazamiento en bytes de *memberName* desde el principio de la estructura especificada por *structName* como un valor de tipo **size_t**. Puede especificar tipos con la palabra clave **struct** .

> [!NOTE]
> **PosiciónInicial** no es una función y no se puede describir mediante un prototipo de C.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
