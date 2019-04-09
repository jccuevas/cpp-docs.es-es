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
ms.openlocfilehash: e1ece6d6f4040b81b55d8400407d46f165b56b53
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024522"
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

`_enable` indica al procesador para establecer la marca de interrupción. En sistemas x86, esta función genera la instrucción Establecer marca de interrupción (`sti`).

Esta función solo está disponible en modo kernel. Si se utiliza en modo de usuario, se produce una excepción Instrucción privilegiada.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)