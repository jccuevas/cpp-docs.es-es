---
title: __vmx_vmlaunch
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmlaunch
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
ms.openlocfilehash: 37f3a39ee7b0d4d24f26fab2347ac9fca020ec47
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037058"
---
# <a name="vmxvmlaunch"></a>__vmx_vmlaunch

**Específicos de Microsoft**

Coloca la aplicación que realiza la llamada en estado de operación que no es de raíz VMX (máquina virtual escriba) mediante el uso de la estructura de control de máquina virtual (VMCS) actual.

## <a name="syntax"></a>Sintaxis

```
unsigned char __vmx_vmlaunch(
   void);
```

## <a name="return-value"></a>Valor devuelto

|Valor|Significado|
|-----------|-------------|
|0|La operación se realizó correctamente.|
|1|Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.|
|2|Error en la operación sin estado disponible.|

## <a name="remarks"></a>Comentarios

Una aplicación puede realizar una operación de entrada en máquina virtual mediante el uso del [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) o [__vmx_vmresume](../intrinsics/vmx-vmresume.md) función. El [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) función puede utilizarse solo con una VMCS cuyo estado de inicio es `Clear`y el [__vmx_vmresume](../intrinsics/vmx-vmresume.md) función puede utilizarse solo con una VMCS cuyo estado de inicio es `Launched`. Por lo tanto, use el [__vmx_vmclear](../intrinsics/vmx-vmclear.md) función para establecer el estado de inicio de una VMCS en `Clear`y, a continuación, utilice el [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) función para la primera operación escriba a la máquina virtual y el [__vmx_vmresume](../intrinsics/vmx-vmresume.md) función para operaciones posteriores.

La función `__vmx_vmlaunch` equivale a la instrucción máquina `VMLAUNCH` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization Technical especificación para la arquitectura IA-32 Intel," documento C97063-002, número en el [Intel Corporation](https://software.intel.com/articles/intel-sdm) sitio.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__vmx_vmlaunch`|x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)<br/>
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)