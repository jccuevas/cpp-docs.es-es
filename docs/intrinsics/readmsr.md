---
title: __readmsr
ms.date: 09/02/2019
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 4398b9d42369e3a914dbec1ed2d14cafecf58483
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222340"
---
# <a name="__readmsr"></a>__readmsr

**Específicos de Microsoft**

Genera la `rdmsr` instrucción, que lee el registro específico del modelo especificado por `register` y devuelve su valor.

## <a name="syntax"></a>Sintaxis

```C
__int64 __readmsr(
   int register
);
```

### <a name="parameters"></a>Parámetros

*el*\
de Registro específico del modelo que se va a leer.

## <a name="return-value"></a>Valor devuelto

Valor del registro especificado.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readmsr`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Esta función solo está disponible en modo kernel y la rutina solo está disponible como intrínseco.

Para obtener más información, consulte la documentación de AMD.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
