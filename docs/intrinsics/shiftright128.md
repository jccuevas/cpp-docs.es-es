---
title: __shiftright128
ms.date: 11/04/2016
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: 8c35625efa9ddc4cf5de3900c6e3e37047b2aa10
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332158"
---
# <a name="shiftright128"></a>__shiftright128

**Específicos de Microsoft**

Desplaza una cantidad de 128 bits, representada como dos cantidades de 64 bits `LowPart` y `HighPart`, a la derecha según un número de bits especificado por `Shift` y devuelve los 64 bits inferiores del resultado.

## <a name="syntax"></a>Sintaxis

```
unsigned __int64 __shiftright128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

#### <a name="parameters"></a>Parámetros

*Parte inferior*<br/>
[in] Los 64 bits inferiores de la cantidad de 128 bits para desplazar.

*HighPart*<br/>
[in] Los 64 bits superiores de la cantidad de 128 bits para desplazar.

*Mayús*<br/>
[in] El número de bits del desplazamiento.

## <a name="return-value"></a>Valor devuelto

Los 64 bits inferiores del resultado.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__shiftright128`|x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

El valor `Shift` es siempre módulo 64 para que, por ejemplo, si se llama a `__shiftright128(0, 1, 64)`, la función desplace los bits `0` de la parte alta a la derecha y devuelva una parte baja de `0` en vez de `1`, como cabría esperar.

## <a name="example"></a>Ejemplo

Para obtener un ejemplo, vea [__shiftleft128](../intrinsics/shiftleft128.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__shiftleft128](../intrinsics/shiftleft128.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)