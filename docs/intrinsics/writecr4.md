---
title: __writecr4
ms.date: 09/02/2019
f1_keywords:
- _writecr4
helpviewer_keywords:
- _writecr4 intrinsic
ms.assetid: ab7651d7-b86b-4be7-a0a0-7263099c70fc
ms.openlocfilehash: 1afdadcdfdbf1060c87e3865dd5597b0b9a2ea6b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219269"
---
# <a name="__writecr4"></a>__writecr4

**Específicos de Microsoft**

Escribe el valor `Data` en el registro CR4.

## <a name="syntax"></a>Sintaxis

```C
void writecr4(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parámetros

*Data*\
de Valor que se va a escribir en el registro CR4.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__writecr4`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Este intrínseco solo está disponible en modo kernel, y la rutina solo está disponible como intrínseco.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
