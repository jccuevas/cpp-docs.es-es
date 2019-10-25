---
title: __writecr8
ms.date: 09/02/2019
f1_keywords:
- _writecr8
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
ms.openlocfilehash: c8df13c15b5cd8a51b77d65ad930a1852809ee30
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219243"
---
# <a name="__writecr8"></a>__writecr8

**Específicos de Microsoft**

Escribe el valor `Data` en el registro CR8.

## <a name="syntax"></a>Sintaxis

```C
void writecr8(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parámetros

*Data*\
de Valor que se va a escribir en el registro CR8.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__writecr8`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El `__writecr8` intrínseco solo está disponible en modo kernel y la rutina solo está disponible como intrínseco.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
