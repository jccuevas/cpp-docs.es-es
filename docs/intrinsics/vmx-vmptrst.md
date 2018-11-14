---
title: __vmx_vmptrst
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmptrst
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
ms.openlocfilehash: 4d7e2ed29daac276c9b6cba07a727371a212fd4a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331898"
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

### <a name="parameters"></a>Parámetros

*VmcsPhysicalAddress*<br/>
[in] La dirección donde se almacena el puntero de la VMCS actual.

## <a name="remarks"></a>Comentarios

El puntero de la VMCS es una dirección física de 64 bits.

La función `__vmx_vmptrst` equivale a la instrucción máquina `VMPTRST` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization Technical especificación para la arquitectura IA-32 Intel," documento C97063-002, número en el [Intel Corporation](https://software.intel.com/articles/intel-sdm) sitio.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__vmx_vmptrst`|x86, x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)