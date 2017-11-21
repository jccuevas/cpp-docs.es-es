---
title: __vmx_vmresume | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __vmx_vmresume
dev_langs: C++
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0a7b59d5b3dce39b85f5c27847b3719d76071961
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="vmxvmresume"></a>__vmx_vmresume
**Específicos de Microsoft**  
  
 Reanuda la operación que no es de raíz VMX mediante la estructura de control de máquina virtual (VMCS) actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned char __vmx_vmresume(  
   void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
  
|Valor|Significado|  
|-----------|-------------|  
|0|La operación se realizó correctamente.|  
|1|Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.|  
|2|Error en la operación sin estado disponible.|  
  
## <a name="remarks"></a>Comentarios  
 Una aplicación puede realizar una operación entrada en máquina virtual mediante la función [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) o `__vmx_vmresume` . La función `__vmx_vmlaunch` solo puede usarse con una VMCS cuyo estado de inicio es `Clear`, y la función `__vmx_vmresume` solo puede usarse con una VMCS cuyo estado de inicio es `Launched`. Por lo tanto, use la función [__vmx_vmclear](../intrinsics/vmx-vmclear.md) para establecer el estado de inicio de una VMCS en `Clear`y luego use la función `__vmx_vmlaunch` para la primera operación de entrada en VM y la función `__vmx_vmresume` para las operaciones subsiguientes de entrada en VM.  
  
 La función `__vmx_vmresume` equivale a la instrucción máquina `VMRESUME` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento PDF, "Intel Virtualization Technical Specification for the IA-32 Intel Architecture" (especificación técnica de virtualización de Intel para la arquitectura IA-32 de Intel), número de documento C97063-002 en el sitio web de [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127)  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__vmx_vmresume`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [__vmx_vmclear](../intrinsics/vmx-vmclear.md)