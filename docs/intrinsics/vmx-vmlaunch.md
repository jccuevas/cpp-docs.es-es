---
title: __vmx_vmlaunch | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmlaunch
dev_langs:
- C++
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 926195aa8dc612d3972634f8140ce3fff753a48f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335028"
---
# <a name="vmxvmlaunch"></a>__vmx_vmlaunch
**Específicos de Microsoft**  
  
 Coloca la aplicación que realiza la llamada en estado de operación que no es de raíz VMX (escriba VM) mediante el uso de la estructura de control de máquina virtual (VMCS) actual.  
  
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
 Una aplicación puede realizar una operación de entrada en máquina virtual utilizando la [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) o [__vmx_vmresume](../intrinsics/vmx-vmresume.md) (función). El [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) función puede utilizarse solo con una VMCS cuyo estado de inicio es `Clear`y el [__vmx_vmresume](../intrinsics/vmx-vmresume.md) función puede utilizarse solo con una VMCS cuyo estado de inicio es `Launched`. Por consiguiente, utilice la [__vmx_vmclear](../intrinsics/vmx-vmclear.md) función para establecer el estado de inicio de una VMCS a `Clear`y, a continuación, use la [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) función para la primera operación de entrada en máquina virtual y el [__vmx_vmresume](../intrinsics/vmx-vmresume.md) función para las operaciones de entrada en máquina virtual posteriores.  
  
 El `__vmx_vmlaunch` función es equivalente a la `VMLAUNCH` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization técnica especificación para la arquitectura IA-32 Intel," documento número C97063-002 en el [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__vmx_vmlaunch`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)   
 [__vmx_vmclear](../intrinsics/vmx-vmclear.md)