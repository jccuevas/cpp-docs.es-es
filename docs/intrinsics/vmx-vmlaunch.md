---
title: __vmx_vmlaunch
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmlaunch
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
ms.openlocfilehash: 8d78e5181fdd43e10431e12d0cf540c8c9c2e719
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219552"
---
# <a name="__vmx_vmlaunch"></a>__vmx_vmlaunch

**Específicos de Microsoft**

Coloca la aplicación que realiza la llamada en el estado de la operación sin raíz VMX (máquina virtual) mediante la estructura de control de máquina virtual (VMCS) actual.

## <a name="syntax"></a>Sintaxis

```C
unsigned char __vmx_vmlaunch(void);
```

## <a name="return-value"></a>Valor devuelto

|Value|Significado|
|-----------|-------------|
|0|La operación se realizó correctamente.|
|1|Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.|
|2|Error en la operación sin estado disponible.|

## <a name="remarks"></a>Comentarios

Una aplicación puede realizar una operación de entrada de máquina virtual mediante la función [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) o [__vmx_vmresume](../intrinsics/vmx-vmresume.md) . La función [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) solo se puede usar con una VMCS cuyo estado de inicio `Clear`es, y la función [__vmx_vmresume](../intrinsics/vmx-vmresume.md) solo se puede usar con una VMCS cuyo estado de `Launched`inicio es. Por lo tanto, use la función [__vmx_vmclear](../intrinsics/vmx-vmclear.md) para establecer el estado de inicio de un `Clear`VMCS en y, después, use la función [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) para su primera operación de entrada de máquina virtual y la función [__vmx_vmresume](../intrinsics/vmx-vmresume.md) para la siguiente máquina virtual-entrar. operaciones.

La función `__vmx_vmlaunch` equivale a la instrucción máquina `VMLAUNCH` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "Especificación técnica de virtualización de Intel para la arquitectura IA-32 Intel", número de documento C97063-002, en el sitio de [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__vmx_vmlaunch`|x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
