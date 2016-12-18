---
title: "__vmx_vmlaunch | Microsoft Docs"
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
  - "__vmx_vmlaunch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMLAUNCH (instrucción)"
  - "__vmx_vmlaunch (función intrínseca)"
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __vmx_vmlaunch
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Coloca la aplicación de VMX estado de la operación de raíz \(VM entra\) mediante la estructura de control actual de la máquina virtual \(VMCS\).  
  
## Sintaxis  
  
```  
unsigned char __vmx_vmlaunch(  
   void);  
```  
  
## Valor devuelto  
  
|Valor|Significado|  
|-----------|-----------------|  
|0|La operación correcta.|  
|1|Se produjo un error en la operación con el estado extendido disponibles en `VM-instruction error field` actual de VMCS.|  
|2|Se produjo un error en la operación sin el estado disponibles.|  
  
## Comentarios  
 Una aplicación puede realizar una operación de VM\-Entrar mediante [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) o la función de [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) .  La función de [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) sólo se puede utilizar con un VMCS cuyo estado de inicio es `Clear`, y la función de [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) sólo se puede utilizar con un VMCS cuyo estado de inicio es `Launched`.  Por consiguiente, utilice la función de [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md) para establecer el estado de la versión de un VMCS a `Clear`, y utilice la función de [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) para la primera operación de VM\-Entrar y la función de [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) para las operaciones posteriores de VM\-Entrar.  
  
 La función de `__vmx_vmlaunch` es equivalente a la instrucción máquina de `VMLAUNCH` .  Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “especificación de Intel Virtualization Técnico para la arquitectura de IA\-32 Intel,” número de documento C97063\-002, en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__vmx_vmlaunch`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md)   
 [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md)