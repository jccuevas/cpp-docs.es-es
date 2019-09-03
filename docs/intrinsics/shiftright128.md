---
title: __shiftright128
ms.date: 09/02/2019
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: a18a9958a51f291e4997c23e87ee48f739562416
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220018"
---
# <a name="__shiftright128"></a>__shiftright128

**Específicos de Microsoft**

Desplaza una cantidad de 128 bits, representada como dos cantidades de 64 bits `LowPart` y `HighPart`, a la derecha según un número de bits especificado por `Shift` y devuelve los 64 bits inferiores del resultado.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 __shiftright128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>Parámetros

*LowPart*\
de Los bits 64 bajos de la cantidad de 128 bits que se va a desplazar.

*HighPart*\
de Los bits 64 altos de la cantidad de 128 bits que se va a desplazar.

*Mover*\
de Número de bits que se va a desplazar.

## <a name="return-value"></a>Valor devuelto

Los 64 bits inferiores del resultado.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__shiftright128`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El valor `Shift` es siempre módulo 64 para que, por ejemplo, si se llama a `__shiftright128(0, 1, 64)`, la función desplace los bits `0` de la parte alta a la derecha y devuelva una parte baja de `0` en vez de `1`, como cabría esperar.

## <a name="example"></a>Ejemplo

Para obtener un ejemplo, vea [shiftleft128](../intrinsics/shiftleft128.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__shiftleft128](../intrinsics/shiftleft128.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
