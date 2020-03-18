---
title: __inword
ms.date: 09/02/2019
f1_keywords:
- __inword_cpp
- __inword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: 7daaf1abd5089716061f118e30e9534e5c5c18ee
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440976"
---
# <a name="__inword"></a>__inword

**Específicos de Microsoft**

Lee datos del puerto especificado mediante la instrucción `in`.

## <a name="syntax"></a>Sintaxis

```C
unsigned short __inword(
   unsigned short Port
);
```

### <a name="parameters"></a>Parámetros

\ de *Puerto*
de Puerto desde el que se va a leer.

## <a name="return-value"></a>Valor devuelto

La palabra de lectura de datos.

## <a name="requirements"></a>Requisitos

|Intrinsic|Architecture|
|---------------|------------------|
|`__inword`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Observaciones

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
