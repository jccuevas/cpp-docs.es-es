---
title: "__vmx_on | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_on"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMXON (instrucción)"
  - "__vmx_on (función intrínseca)"
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_on
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Provoca la operación de las extensiones de la máquina virtual \(VMX\) del procesador.  
  
## Sintaxis  
  
```  
unsigned char __vmx_on(  
   unsigned __int64 *VmsSupportPhysicalAddress  
);  
```  
  
#### Parámetros  
 \[in\] `VmsSupportPhysicalAddress`  
 Un puntero a una dirección física 64 bits que apunta a una estructura de control de la máquina \(VMCS\) virtual.  
  
## Valor devuelto  
  
|Valor|Significado|  
|-----------|-----------------|  
|0|La operación correcta.|  
|1|Se produjo un error en la operación con el estado extendido disponibles en `VM-instruction error field` actual de VMCS.|  
|2|Se produjo un error en la operación sin el estado disponibles.|  
  
## Comentarios  
 La función de `__vmx_on` corresponde a la instrucción máquina de `VMXON` .  Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “especificación de Intel Virtualization Técnico para la arquitectura de IA\-32 Intel,” número de documento C97063\-002, en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__vmx_on`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)