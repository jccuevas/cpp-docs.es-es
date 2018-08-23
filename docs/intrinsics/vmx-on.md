---
title: __vmx_on | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_on
dev_langs:
- C++
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e01be3d3f7db075116782b64e8b92ba12fb02f1d
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42544514"
---
# <a name="vmxon"></a>__vmx_on
**Específicos de Microsoft**  
  
 Activa la operación de extensiones (VMX) de la máquina virtual en el procesador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned char __vmx_on(  
   unsigned __int64 *VmsSupportPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `VmsSupportPhysicalAddress`  
 Un puntero a una dirección física de 64 bits que señala a una estructura de control de máquina virtual (VMCS).  
  
## <a name="return-value"></a>Valor devuelto  
  
|Valor|Significado|  
|-----------|-------------|  
|0|La operación se realizó correctamente.|  
|1|Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.|  
|2|Error en la operación sin estado disponible.|  
  
## <a name="remarks"></a>Comentarios  
 El `__vmx_on` función corresponde a la `VMXON` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization Technical especificación para la arquitectura IA-32 Intel," documento C97063-002, número en el [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__vmx_on`|x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)