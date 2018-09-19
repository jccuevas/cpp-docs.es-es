---
title: __vmx_vmclear | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmclear
dev_langs:
- C++
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd5661a2b6aa257c91babcc3d17b1babb0b4d2c2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707166"
---
# <a name="vmxvmclear"></a>__vmx_vmclear
**Específicos de Microsoft**  
  
 Inicializa la estructura de control de máquina virtual especificada (VMCS) y establece su estado de inicio en `Clear`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned char __vmx_vmclear(  
   unsigned __int64 *VmcsPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*VmcsPhysicalAddress*|[in] Un puntero a una ubicación de memoria de 64 bits que contiene la dirección física de la VMCS para borrar.|  
  
## <a name="return-value"></a>Valor devuelto  
  
|Valor|Significado|  
|-----------|-------------|  
|0|La operación se realizó correctamente.|  
|1|Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.|  
|2|Error en la operación sin estado disponible.|  
  
## <a name="remarks"></a>Comentarios  
 Una aplicación puede realizar una operación de entrada en máquina virtual mediante el uso del [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) o [__vmx_vmresume](../intrinsics/vmx-vmresume.md) función. El [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) función puede utilizarse solo con una VMCS cuyo estado de inicio es `Clear`y el [__vmx_vmresume](../intrinsics/vmx-vmresume.md) función puede utilizarse solo con una VMCS cuyo estado de inicio es `Launched`. Por lo tanto, use el [__vmx_vmclear](../intrinsics/vmx-vmclear.md) función para establecer el estado de inicio de una VMCS en `Clear`. Use la [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) función para la primera operación escriba a la máquina virtual y el [__vmx_vmresume](../intrinsics/vmx-vmresume.md) función para operaciones posteriores.  
  
 El `__vmx_vmclear` función es equivalente a la `VMCLEAR` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization Technical especificación para la arquitectura IA-32 Intel," documento C97063-002, número en el [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__vmx_vmclear`|x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)