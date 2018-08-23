---
title: __svm_vmsave | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmsave
dev_langs:
- C++
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54cc51ee320c6b942c3ff0563f293cf48d1c34db
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539299"
---
# <a name="svmvmsave"></a>__svm_vmsave
**Específicos de Microsoft**  
  
 Almacena un subconjunto de estado del procesador en el bloque de control de máquina virtual especificada (VMCB).  
  
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
 El `__svm_vmsave` función es equivalente a la `VMSAVE` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "volumen de Manual de programadores de arquitecturas AMD64 2: sistema de programación," número de documento 24593, revisión 3.11 o posterior, en el [AMD Corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__svm_vmsave`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmrun](../intrinsics/svm-vmrun.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)