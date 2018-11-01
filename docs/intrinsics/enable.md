---
title: _enable
ms.date: 11/04/2016
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 1d129db17b489972555efb0b5df2de52e01fa649
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631257"
---
# <a name="enable"></a>_enable

**Específicos de Microsoft**

Habilita las interrupciones.

## <a name="syntax"></a>Sintaxis

```
void _enable(void);
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_enable`|x86, ARM, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

`_enable` indica al procesador que establezca el indicador de interrupción. En sistemas x86, esta función genera la instrucción Establecer marca de interrupción (`sti`).

Esta función solo está disponible en modo kernel. Si se utiliza en modo de usuario, se produce una excepción Instrucción privilegiada.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)