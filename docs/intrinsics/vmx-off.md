---
title: "__vmx_off | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_off"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMXOFF (instrucción)"
  - "__vmx_off (función intrínseca)"
ms.assetid: 78a32d46-9291-406c-b982-a550855aff18
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_off
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Desactiva la operación de las extensiones de la máquina virtual \(VMX\) del procesador.  
  
## Sintaxis  
  
```  
void __vmx_off();  
```  
  
## Comentarios  
 La función de `__vmx_off` es equivalente a la instrucción máquina de `VMXOFF` .  Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “especificación de Intel Virtualization Técnico para la arquitectura de IA\-32 Intel,” número de documento C97063\-002, en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__vmx_off`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)