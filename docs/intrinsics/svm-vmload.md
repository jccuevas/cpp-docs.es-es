---
title: __svm_vmload | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __svm_vmload
dev_langs: C++
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9aee6ce3d9a3554e4722a143bcb683c40b78ea14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="svmvmload"></a>__svm_vmload
**Específicos de Microsoft**  
  
 Carga un subconjunto de estado del procesador en el bloque de control de la máquina virtual especificada (VMCB).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __svm_vmload(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `VmcbPhysicalAddress`|La dirección física de la VMCB.|  
  
## <a name="remarks"></a>Comentarios  
 El `__svm_vmload` función es equivalente a la `VMLOAD` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "volumen de Manual del programador de arquitectura AMD64 2: programación de sistema," número 24593, 3.11, de revisión del documento en el [corporation AMD](http://go.microsoft.com/fwlink/?LinkId=23746) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__svm_vmload`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmrun](../intrinsics/svm-vmrun.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)