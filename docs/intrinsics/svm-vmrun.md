---
title: "__svm_vmrun | Microsoft Docs"
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
  - "__svm_vmrun"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__svm_vmrun (función intrínseca)"
  - "VMRUN (instrucción)"
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_vmrun
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Inicia la ejecución de código invitado de máquina virtual que corresponde al bloque de control especificado de la máquina virtual \(VMCB\).  
  
## Sintaxis  
  
```  
void __svm_vmrun(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|\[in\] `VmcbPhysicalAddress`|La dirección física de VMCB.|  
  
## Comentarios  
 La función de `__svm_vmrun` utiliza una cantidad de información mínimo en el VMCB para iniciar ejecutando el código invitado de la máquina virtual.  Utilice la función de [\_\_svm\_vmsave](../intrinsics/svm-vmsave.md) o de [\_\_svm\_vmload](../intrinsics/svm-vmload.md) si necesita más información para controlar una interrupción compleja o para cambiar a otro invitado.  
  
 La función de `__svm_vmrun` es equivalente a la instrucción máquina de `VMRUN` .  Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “volumen 2 de Manual del programador de arquitectura AMD64: Programa del sistema,” número de documento 24593, revisión 3,11 o posterior, en [compañía de AMD](http://go.microsoft.com/fwlink/?LinkId=23746) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__svm_vmrun`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_vmsave](../intrinsics/svm-vmsave.md)   
 [\_\_svm\_vmload](../intrinsics/svm-vmload.md)