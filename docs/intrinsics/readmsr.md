---
title: __readmsr
ms.date: 11/04/2016
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 45e9c21eb8d9ac213812236a91c050c3c9df8f8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641069"
---
# <a name="readmsr"></a>__readmsr

**Específicos de Microsoft**

Genera el `rdmsr` instrucción, que lee el registro específicos del modelo especificado por `register` y devuelve su valor.

## <a name="syntax"></a>Sintaxis

```
__int64 __readmsr( 
   int register 
);
```

#### <a name="parameters"></a>Parámetros

*register*<br/>
[in] El registro específico del modelo para leer.

## <a name="return-value"></a>Valor devuelto

El valor en el registro especificado.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readmsr`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta función sólo está disponible en modo kernel y la rutina solo está disponible como intrínseco.

Para obtener más información, consulte la documentación de AMD.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)