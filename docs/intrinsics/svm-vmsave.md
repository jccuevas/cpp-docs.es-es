---
title: __svm_vmsave | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __svm_vmsave
dev_langs:
- C++
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa5ebe1841522da8a5e2a62ae71ebb9d04b2865
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="svmvmsave"></a>__svm_vmsave
**Específicos de Microsoft**  
  
 Almacena un subconjunto de estado del procesador en el bloque de control de la máquina virtual especificada (VMCB).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __svm_vmsave(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `VmcbPhysicalAddress`|La dirección física de la VMCB.|  
  
## <a name="remarks"></a>Comentarios  
 El `__svm_vmsave` función es equivalente a la `VMSAVE` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "Manual volumen del programador de arquitectura AMD64 2: programación de sistema," número de documento 24593, revisión 3.11 o posterior, en el [Corporation AMD](http://go.microsoft.com/fwlink/p/?linkid=23746) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__svm_vmsave`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmrun](../intrinsics/svm-vmrun.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)