---
title: __readcr4
ms.date: 11/04/2016
f1_keywords:
- __readcr4
helpviewer_keywords:
- __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
ms.openlocfilehash: b67016846768be778881c02b395c8d6f3af1ef3f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037229"
---
# <a name="readcr4"></a>__readcr4

**Específicos de Microsoft**

Lee el registro CR4 y devuelve su valor.

## <a name="syntax"></a>Sintaxis

```
unsigned __int64 __readcr4(void);
```

## <a name="return-value"></a>Valor devuelto

El valor del registro CR4.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readcr4`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Este intrínseco solo está disponible en modo kernel, y la rutina solo está disponible como intrínseco.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)