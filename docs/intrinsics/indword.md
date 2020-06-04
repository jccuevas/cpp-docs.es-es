---
title: __indword
ms.date: 09/02/2019
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: 790b65c8a565124df92b82b7ea17174788086a96
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222118"
---
# <a name="__indword"></a>__indword

**Específicos de Microsoft**

Lee una palabra doble de datos del puerto especificado mediante la `in` instrucción.

## <a name="syntax"></a>Sintaxis

```C
unsigned long __indword(
   unsigned short Port
);
```

### <a name="parameters"></a>Parámetros

*Casilla*\
de Puerto desde el que se va a leer.

## <a name="return-value"></a>Valor devuelto

La Palabra leída del puerto.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__indword`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
