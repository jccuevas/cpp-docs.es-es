---
title: __svm_vmrun | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmrun
dev_langs:
- C++
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4711238c45955ee7067e3e418212bcdb0fae09ca
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538524"
---
# <a name="svmvmrun"></a>__svm_vmrun
**Específicos de Microsoft**  
  
 Inicia la ejecución del código de invitado de máquina virtual que se corresponde con el bloque de control de máquina virtual especificada (VMCB).  
  
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
 El `__svm_vmrun` función usa una cantidad mínima de información en el VMCB para empezar a ejecutar el código de invitado de máquina virtual. Use la [__svm_vmsave](../intrinsics/svm-vmsave.md) o [__svm_vmload](../intrinsics/svm-vmload.md) funcionando si necesita más información para controlar una interrupción compleja o para cambiar a otro invitado.  
  
 El `__svm_vmrun` función es equivalente a la `VMRUN` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "volumen de Manual de programadores de arquitecturas AMD64 2: sistema de programación," número de documento 24593, revisión 3.11 o posterior, en el [corporation AMD](http://go.microsoft.com/fwlink/p/?linkid=23746) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__svm_vmrun`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)