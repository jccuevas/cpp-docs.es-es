---
title: "__vmx_vmwrite | Microsoft Docs"
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
  - "__vmx_vmwrite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__vmx_vmwrite (función intrínseca)"
  - "VMWRITE (instrucción)"
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __vmx_vmwrite
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Escriba el valor especificado en el campo especificado en la estructura de control actual de la máquina \(VMCS\) virtual.  
  
## Sintaxis  
  
```  
unsigned char __vmx_vmwrite(   
   size_t Field,  
   size_t FieldValue  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|\[in\] `Field`|El campo de VMCS a escribir.|  
|\[in\] `FieldValue`|El valor a escribir en el campo de VMCS.|  
  
## Valor devuelto  
 0  
 La operación correcta.  
  
 1  
 Se produjo un error en la operación con el estado extendido disponibles en `VM-instruction error field` actual de VMCS.  
  
 2  
 Se produjo un error en la operación sin el estado disponibles.  
  
## Comentarios  
 La función de `__vmx_vmwrite` es equivalente a la instrucción máquina de `VMWRITE` .  El valor del parámetro de `Field` es un índice codificadas de campo que se describe en la documentación de Intel.  Para obtener más información, busque el documento, “especificación de Intel Virtualization Técnico para la arquitectura de IA\-32 Intel”, el número de documento C97063\-002, en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio y después, vea el apéndice C de ese documento.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__vmx_vmwrite`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmread](../intrinsics/vmx-vmread.md)