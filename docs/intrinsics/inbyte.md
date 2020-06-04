---
title: __inbyte
ms.date: 09/02/2019
f1_keywords:
- __inbyte
- __inbyte_cpp
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
ms.openlocfilehash: f0036763ed7315a54fbfe6dcc873b46b52f0730c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222146"
---
# <a name="__inbyte"></a>__inbyte

**Específicos de Microsoft**

Genera la `in` instrucción, devolviendo una lectura de un solo byte desde el `Port`puerto especificado por.

## <a name="syntax"></a>Sintaxis

```C
unsigned char __inbyte(
   unsigned short Port
);
```

### <a name="parameters"></a>Parámetros

*Casilla*\
de Puerto desde el que se va a leer.

## <a name="return-value"></a>Valor devuelto

Byte leído del puerto especificado.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__inbyte`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
