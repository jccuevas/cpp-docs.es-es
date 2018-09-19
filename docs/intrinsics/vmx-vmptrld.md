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
ms.openlocfilehash: fd04350df17b6d2dfed65526d0f7681c314f07f8
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682625"
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
 El puntero de la VMCS es una dirección física de 64 bits.  
  
 El `__vmx_vmptrld` función es equivalente a la `VMPTRLD` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization Technical especificación para la arquitectura IA-32 Intel," documento C97063-002, número en el [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__vmx_vmptrld`|x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)