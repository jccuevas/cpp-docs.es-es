---
title: __vmx_vmptrld
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 4079eadc1f2d655c14192c8c4286ad240b1c1dbe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571384"
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

### <a name="parameters"></a>Parámetros

*VmcsPhysicalAddress*<br/>
[in] La dirección donde se almacena el puntero VMCS.

## <a name="return-value"></a>Valor devuelto

0<br/>
La operación se realizó correctamente.

1<br/>
Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.

2<br/>
Error en la operación sin estado disponible.

## <a name="remarks"></a>Comentarios

El puntero de la VMCS es una dirección física de 64 bits.

La función `__vmx_vmptrld` equivale a la instrucción máquina `VMPTRLD` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization Technical especificación para la arquitectura IA-32 Intel," documento C97063-002, número en el [Intel Corporation](https://software.intel.com/articles/intel-sdm) sitio.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__vmx_vmptrld`|x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)