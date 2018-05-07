---
title: __vmx_vmptrld | Documentos de Microsoft
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
ms.openlocfilehash: 599e15414a944602ee196f3910a1c5dd561c906d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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
 [in] *`VmcsPhysicalAddress`  
 La dirección donde se almacena el puntero VMCS.  
  
## <a name="return-value"></a>Valor devuelto  
 0  
 La operación se realizó correctamente.  
  
 1  
 Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.  
  
 2  
 Error en la operación sin estado disponible.  
  
## <a name="remarks"></a>Comentarios  
 El puntero VMCS es una dirección física de 64 bits.  
  
 El `__vmx_vmptrld` función es equivalente a la `VMPTRLD` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization técnica especificación para la arquitectura IA-32 Intel," documento número C97063-002 en el [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__vmx_vmptrld`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)