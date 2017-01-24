---
title: "__vmx_vmclear | Microsoft Docs"
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
  - "__vmx_vmclear"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMCLEAR (instrucción)"
  - "__vmx_vmclear (función intrínseca)"
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __vmx_vmclear
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Inicializa la estructura de control especificada de la \(VMCS\) máquina virtual y establece su estado de inicio para `Clear`.  
  
## Sintaxis  
  
```  
unsigned char __vmx_vmclear(  
   unsigned __int64 *VmcsPhysicalAddress  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|\[in\] `VmcsPhysicalAddress`|Un puntero a una ubicación de memoria de 64 bits que contiene la dirección física de VMCS borrar.|  
  
## Valor devuelto  
  
|Valor|Significado|  
|-----------|-----------------|  
|0|La operación correcta.|  
|1|Se produjo un error en la operación con el estado extendido disponibles en `VM-instruction error field` actual de VMCS.|  
|2|Se produjo un error en la operación sin el estado disponibles.|  
  
## Comentarios  
 Una aplicación puede realizar una operación de VM\-Entrar mediante [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) o la función de [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) .  La función de [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) sólo se puede utilizar con un VMCS cuyo estado de inicio es `Clear`, y la función de [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) sólo se puede utilizar con un VMCS cuyo estado de inicio es `Launched`.  Por consiguiente, utilice la función de [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md) para establecer el estado de la versión de un VMCS a `Clear`.  Utilice la función de [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) para la primera operación de VM\-Entrar y la función de [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) para las operaciones posteriores de VM\-Entrar.  
  
 La función de `__vmx_vmclear` es equivalente a la instrucción máquina de `VMCLEAR` .  Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “especificación de Intel Virtualization Técnico para la arquitectura de IA\-32 Intel,” número de documento C97063\-002, en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__vmx_vmclear`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md)