---
title: "__vmx_vmptrst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_vmptrst"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__vmx_vmptrst (función intrínseca)"
  - "VMPTRST (instrucción)"
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_vmptrst
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Almacena el puntero a la estructura de control actual de la máquina virtual \(VMCS\) en la dirección especificada.  
  
## Sintaxis  
  
```  
void __vmx_vmptrst(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### Parámetros  
 \[in\] \*`VmcsPhysicalAddress`  
 La dirección donde se almacena el puntero de la actual VMCS.  
  
## Comentarios  
 El puntero de VMCS es una dirección física de 64 bits.  
  
 La función de `__vmx_vmptrst` es equivalente a la instrucción máquina de `VMPTRST` .  Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “especificación de Intel Virtualization Técnico para la arquitectura de IA\-32 Intel,” número de documento C97063\-002, en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__vmx_vmptrst`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmptrld](../intrinsics/vmx-vmptrld.md)