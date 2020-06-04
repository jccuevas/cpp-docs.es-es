---
title: __readpmc
ms.date: 09/02/2019
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: af0f1874d991771423ddebfedd4624cd0b71760f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221038"
---
# <a name="__readpmc"></a>__readpmc

**Específicos de Microsoft**

Genera la `rdpmc` instrucción, que lee el contador de supervisión de rendimiento especificado por *Counter*.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 __readpmc(
   unsigned long counter
);
```

### <a name="parameters"></a>Parámetros

*bloque*\
de El contador de rendimiento que se va a leer.

## <a name="return-value"></a>Valor devuelto

Valor del contador de rendimiento especificado.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readpmc`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El intrínseco solo está disponible en modo kernel y la rutina solo está disponible como intrínseco.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
