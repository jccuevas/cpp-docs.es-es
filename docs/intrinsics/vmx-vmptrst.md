---
title: __vmx_vmptrst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrst
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccd691edb9ee799c8585fb33cb6b837e2871fc36
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413982"
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst

**Específicos de Microsoft**

Almacena el puntero a la estructura de control de máquina virtual (VMCS) actual en la dirección especificada.

## <a name="syntax"></a>Sintaxis

```
void __vmx_vmptrst( 
   unsigned __int64 *VmcsPhysicalAddress 
);
```

#### <a name="parameters"></a>Parámetros

[in] *`VmcsPhysicalAddress` la dirección donde se almacena el puntero de la VMCS actual.

## <a name="remarks"></a>Comentarios

El puntero de la VMCS es una dirección física de 64 bits.

El `__vmx_vmptrst` función es equivalente a la `VMPTRST` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization Technical especificación para la arquitectura IA-32 Intel," documento C97063-002, número en el [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) sitio.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__vmx_vmptrst`|x86, x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)