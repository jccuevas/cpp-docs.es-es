---
title: __vmx_on
ms.date: 09/02/2019
f1_keywords:
- __vmx_on
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
ms.openlocfilehash: b6041711d9b6806362b856475151f2c4f63750cb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219576"
---
# <a name="__vmx_on"></a>__vmx_on

**Específicos de Microsoft**

Activa la operación de las extensiones de máquina virtual (VMX) en el procesador.

## <a name="syntax"></a>Sintaxis

```C
unsigned char __vmx_on(
   unsigned __int64 *VmsSupportPhysicalAddress
);
```

### <a name="parameters"></a>Parámetros

*VmsSupportPhysicalAddress*\
de Un puntero a una dirección física de 64 bits que apunta a una estructura de control de máquina virtual (VMCS).

## <a name="return-value"></a>Valor devuelto

|Valor|Significado|
|-----------|-------------|
|0|La operación se realizó correctamente.|
|1|Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.|
|2|Error en la operación sin estado disponible.|

## <a name="remarks"></a>Comentarios

La `__vmx_on` función corresponde a la `VMXON` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "Especificación técnica de virtualización de Intel para la arquitectura IA-32 Intel", número de documento C97063-002, en el sitio de [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__vmx_on`|x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
