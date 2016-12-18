---
title: "__svm_vmload | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__svm_vmload"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__svm_vmload (función intrínseca)"
  - "VMLOAD (instrucción)"
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_vmload
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Carga un subconjunto de estado de procesador del bloque de control especificado de la máquina \(VMCB\) virtual.  
  
## Sintaxis  
  
```  
void __svm_vmload(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|\[in\] `VmcbPhysicalAddress`|La dirección física de VMCB.|  
  
## Comentarios  
 La función de `__svm_vmload` es equivalente a la instrucción máquina de `VMLOAD` .  Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “volumen 2 de Manual del programador de arquitectura AMD64: Programa del sistema,” número de documento 24593, revisión 3,11, en [compañía de AMD](http://go.microsoft.com/fwlink/?LinkId=23746) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__svm_vmload`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_vmrun](../intrinsics/svm-vmrun.md)   
 [\_\_svm\_vmsave](../intrinsics/svm-vmsave.md)