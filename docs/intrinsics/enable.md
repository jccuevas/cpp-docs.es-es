---
title: _enable
ms.date: 09/02/2019
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 7adcd4eac807b8d0937efbbe6d89f8ad6dcb157c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217874"
---
# <a name="_enable"></a>_enable

**Específicos de Microsoft**

Habilita las interrupciones.

## <a name="syntax"></a>Sintaxis

```C
void _enable(void);
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_enable`|x86, ARM, x64, ARM64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

`_enable` indica al procesador que establezca el indicador de interrupción. En sistemas x86, esta función genera la instrucción Establecer marca de interrupción (`sti`).

Esta función solo está disponible en modo kernel. Si se utiliza en modo de usuario, se produce una excepción Instrucción privilegiada.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
