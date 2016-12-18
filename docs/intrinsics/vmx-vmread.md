---
title: "__vmx_vmread | Microsoft Docs"
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
  - "__vmx_vmread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMREAD (instrucción)"
  - "__vmx_vmread (función intrínseca)"
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __vmx_vmread
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Lee un campo específico de la estructura de control y los lugares \(VMCS\) actuales de la máquina virtual él en la ubicación especificada.  
  
## Sintaxis  
  
```  
unsigned char __vmx_vmread(  
   size_t Field,  
   size_t *FieldValue  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|\[in\] `Field`|El campo de VMCS a leer.|  
|\[in\] `FieldValue`|Un puntero a la ubicación para almacenar la lectura del valor del campo de VMCS especificado por el parámetro de `Field` .|  
  
## Valor devuelto  
  
|Valor|Significado|  
|-----------|-----------------|  
|0|La operación correcta.|  
|1|Se produjo un error en la operación con el estado extendido disponibles en `VM-instruction error field` actual de VMCS.|  
|2|Se produjo un error en la operación sin el estado disponibles.|  
  
## Comentarios  
 La función de `__vmx_vmread` es equivalente a la instrucción máquina de `VMREAD` .  El valor del parámetro de `Field` es un índice codificadas de campo que se describe en la documentación de Intel.  Para obtener más información, busque el documento, “especificación de Intel Virtualization Técnico para la arquitectura de IA\-32 Intel”, el número de documento C97063\-002, en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio, entonces consulta el apéndice C de ese documento.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__vmx_vmread`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmwrite](../intrinsics/vmx-vmwrite.md)