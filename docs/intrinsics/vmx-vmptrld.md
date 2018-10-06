---
title: __vmx_vmptrld | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrld
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f3304106662d290a208545061bf9f71b7f30c10
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820950"
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld

**Específicos de Microsoft**

Carga el puntero a la estructura de control de máquina virtual (VMCS) actual de la dirección especificada.

## <a name="syntax"></a>Sintaxis

```
int __vmx_vmptrld( 
   unsigned __int64 *VmcsPhysicalAddress 
);
```

#### <a name="parameters"></a>Parámetros

[in] *`VmcsPhysicalAddress` la dirección donde se almacena el puntero VMCS.

## <a name="return-value"></a>Valor devuelto

0 de la operación se realizó correctamente.

1 error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.

2 no se pudo la operación sin estado disponible.

## <a name="remarks"></a>Comentarios

El puntero de la VMCS es una dirección física de 64 bits.

El `__vmx_vmptrld` función es equivalente a la `VMPTRLD` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization Technical especificación para la arquitectura IA-32 Intel," documento C97063-002, número en el [Intel Corporation](https://software.intel.com/articles/intel-sdm) sitio.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__vmx_vmptrld`|x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)