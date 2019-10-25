---
title: __nop
ms.date: 09/02/2019
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 4561bcb84063f3707825c8ca164867d41500e2db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221676"
---
# <a name="__nop"></a>__nop

**Específicos de Microsoft**

Genera código máquina específico de la plataforma que no realiza ninguna operación.

## <a name="syntax"></a>Sintaxis

```C
void __nop();
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__nop`|x86, ARM, x64, ARM64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="remarks"></a>Comentarios

La función `__nop` equivale a la instrucción máquina `NOP` . Para obtener más información sobre x86 y x64, busque el documento "manual del desarrollador de software de arquitectura Intel, volumen 2: Referencia del conjunto de instrucciones, en el sitio de [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__noop](../intrinsics/noop.md)
