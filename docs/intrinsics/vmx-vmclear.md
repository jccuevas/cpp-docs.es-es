---
title: __vmx_vmclear
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 3b5807402cf0a9d8a9ef1ded1d112d22a801633e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219543"
---
# <a name="__vmx_vmclear"></a>__vmx_vmclear

**Específicos de Microsoft**

Inicializa la estructura de control de máquina virtual (VMCS) especificada y establece su estado de `Clear`Inicio en.

## <a name="syntax"></a>Sintaxis

```C
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Parámetros

*VmcsPhysicalAddress*\
de Puntero a una ubicación de memoria de 64 bits que contiene la dirección física del VMCS que se va a borrar.

## <a name="return-value"></a>Valor devuelto

|Valor|Significado|
|-----------|-------------|
|0|La operación se realizó correctamente.|
|1|Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.|
|2|Error en la operación sin estado disponible.|

## <a name="remarks"></a>Comentarios

Una aplicación puede realizar una operación de entrada de máquina virtual mediante la función [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) o [__vmx_vmresume](../intrinsics/vmx-vmresume.md) . La función [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) solo se puede usar con una VMCS cuyo estado de inicio `Clear`es, y la función [__vmx_vmresume](../intrinsics/vmx-vmresume.md) solo se puede usar con una VMCS cuyo estado de `Launched`inicio es. Por lo tanto, use la función [__vmx_vmclear](../intrinsics/vmx-vmclear.md) para establecer el estado de inicio de un `Clear`VMCS en. Use la función [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) para su primera operación de entrada de máquina virtual y la función [__vmx_vmresume](../intrinsics/vmx-vmresume.md) para las operaciones posteriores de la máquina virtual.

La función `__vmx_vmclear` equivale a la instrucción máquina `VMCLEAR` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "Especificación técnica de virtualización de Intel para la arquitectura IA-32 Intel", número de documento C97063-002, en el sitio de [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__vmx_vmclear`|x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)
