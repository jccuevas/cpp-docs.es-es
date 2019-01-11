---
title: __nop
ms.date: 11/04/2016
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: b0033b0e3a62a16c2856b0e25daeebdb5df0c81f
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220392"
---
# <a name="nop"></a>__nop

**Específicos de Microsoft**

Genera código máquina específico de plataforma que no realiza ninguna operación.

## <a name="syntax"></a>Sintaxis

```
void __nop();
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__nop`|x86, ARM, x64, ARM64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="remarks"></a>Comentarios

La función `__nop` equivale a la instrucción máquina `NOP` . Para obtener más información sobre x86 y x64, busque el documento, "Manual del desarrollador de Software de arquitectura Intel, volumen 2: Establecer referencia de instrucciones,"en el [Intel Corporation](https://software.intel.com/articles/intel-sdm) sitio.

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__noop](../intrinsics/noop.md)
