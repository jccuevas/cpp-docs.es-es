---
title: __readcr2
ms.date: 11/04/2016
f1_keywords:
- __readcr2
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
ms.openlocfilehash: e11f6c4fd0f5483b0d47abdaf6b8b371a8c61f09
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496504"
---
# <a name="readcr2"></a>__readcr2

**Específicos de Microsoft**

Lee el registro CR2 y devuelve su valor.

## <a name="syntax"></a>Sintaxis

```
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>Valor devuelto

El valor del registro CR2.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readcr2`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Este intrínseco solo está disponible en modo kernel, y la rutina solo está disponible como intrínseco.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)