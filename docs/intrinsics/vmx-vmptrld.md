---
title: "__vmx_vmptrld | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_vmptrld"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__vmx_vmptrld (función instrínseca)"
  - "VMPTRLD (instrucción)"
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_vmptrld
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Carga el puntero a la estructura de control actual de la máquina virtual \(VMCS\) de la dirección especificada.  
  
## Sintaxis  
  
```  
int __vmx_vmptrld(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### Parámetros  
 \[in\] \*`VmcsPhysicalAddress`  
 La dirección donde se almacena el puntero de VMCS.  
  
## Valor devuelto  
 0  
 La operación correcta.  
  
 1  
 Se produjo un error en la operación con el estado extendido disponibles en `VM-instruction error field` actual de VMCS.  
  
 2  
 Se produjo un error en la operación sin el estado disponibles.  
  
## Comentarios  
 El puntero de VMCS es una dirección física de 64 bits.  
  
 La función de `__vmx_vmptrld` es equivalente a la instrucción máquina de `VMPTRLD` .  Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “especificación de Intel Virtualization Técnico para la arquitectura de IA\-32 Intel,” número de documento C97063\-002, en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__vmx_vmptrld`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmptrst](../intrinsics/vmx-vmptrst.md)