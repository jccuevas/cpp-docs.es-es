---
title: __indword
ms.date: 11/04/2016
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: 063ebd92682f8011bc6b60eee14c3443bc04c333
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029335"
---
# <a name="indword"></a>__indword

**Específicos de Microsoft**

Lee una palabra doble de los datos desde el puerto especificado mediante el `in` instrucción.

## <a name="syntax"></a>Sintaxis

```
unsigned long __indword(
   unsigned short Port
);
```

#### <a name="parameters"></a>Parámetros

*Puerto*<br/>
[in] Para leer desde el puerto.

## <a name="return-value"></a>Valor devuelto

La palabra se lee desde el puerto.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__indword`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)