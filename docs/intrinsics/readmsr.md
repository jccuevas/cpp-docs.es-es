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
ms.openlocfilehash: 891ca43af4a81b63de39d367ea418e43811f78d0
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326412"
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