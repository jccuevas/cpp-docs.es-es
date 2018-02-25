---
title: __svm_vmrun | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __svm_vmrun
dev_langs:
- C++
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 988a045bc957d5920fee7e3e659d7a0b4f02d8d2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="svmvmrun"></a>__svm_vmrun
**Específicos de Microsoft**  
  
 Inicia la ejecución del código de invitado de máquina virtual que se corresponde con el bloque de control de la máquina virtual especificada (VMCB).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __svm_vmrun(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `VmcbPhysicalAddress`|La dirección física de la VMCB.|  
  
## <a name="remarks"></a>Comentarios  
 El `__svm_vmrun` función usa una cantidad mínima de información en el VMCB para comenzar a ejecutar el código de invitado de la máquina virtual. Use la [__svm_vmsave](../intrinsics/svm-vmsave.md) o [__svm_vmload](../intrinsics/svm-vmload.md) funcionar si necesita más información para controlar una interrupción compleja o para cambiar a otro invitado.  
  
 El `__svm_vmrun` función es equivalente a la `VMRUN` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "Manual volumen del programador de arquitectura AMD64 2: programación de sistema," número de documento 24593, revisión 3.11 o posterior, en el [corporation AMD](http://go.microsoft.com/fwlink/p/?linkid=23746) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__svm_vmrun`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)