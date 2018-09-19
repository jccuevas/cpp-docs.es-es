---
title: offsetof Macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 308aac2493751cfe2147187ed9848347124a90d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401469"
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

*Nombre de usuario registrado*<br/>
Nombre del miembro de la estructura de datos primaria cuyo desplazamiento se determina.

## <a name="return-value"></a>Valor devuelto

**offsetof** devuelve el desplazamiento en bytes del miembro especificado desde el principio de su estructura de datos primaria. No se define para campos de bits.

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
