---
title: __invlpg
ms.date: 09/02/2019
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: ba8bd81498f805992336b0dc4163fe18fa157a2c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221897"
---
# <a name="__invlpg"></a>__invlpg

**Específicos de Microsoft**

Genera la instrucción `invlpg` x86, que invalida el búfer de traducción de direcciones (TLB) de la página asociada a la memoria a la que apunta la *Dirección*.

## <a name="syntax"></a>Sintaxis

```C
void __invlpg(
   void* Address
);
```

### <a name="parameters"></a>Parámetros

*Dirección*\
de Una dirección de 64 bits.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__invlpg`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El intrínseco `__invlpg` emite una instrucción privilegiada y solo está disponible en modo kernel con un nivel de privilegios (CPL) de 0.

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
