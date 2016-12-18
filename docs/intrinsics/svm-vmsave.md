---
title: "__svm_vmsave | Microsoft Docs"
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
  - "__svm_vmsave"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMSAVE (instrucción)"
  - "__svm_vmsave (función intrínseca)"
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_vmsave
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Almacena un subconjunto de estado de procesador en el bloque de control especificado de la máquina virtual \(VMCB\).  
  
## Sintaxis  
  
```  
void __svm_vmsave(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|\[in\] `VmcbPhysicalAddress`|La dirección física de VMCB.|  
  
## Comentarios  
 La función de `__svm_vmsave` es equivalente a la instrucción máquina de `VMSAVE` .  Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “volumen 2 de Manual del programador de arquitectura AMD64: Programa del sistema,” número de documento 24593, revisión 3,11 o posterior, en [AMD Corporation](http://go.microsoft.com/fwlink/?LinkId=23746) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__svm_vmsave`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_vmrun](../intrinsics/svm-vmrun.md)   
 [\_\_svm\_vmload](../intrinsics/svm-vmload.md)