---
title: "__svm_skinit | Microsoft Docs"
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
  - "__svm_skinit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SKINIT (instrucción)"
  - "__svm_skinit (función intrínseca)"
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_skinit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Inicia la carga de software comprobable seguro, como una máquina virtual monitor.  
  
## Sintaxis  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`SLB`|La dirección física de 32 bits de un byte de garantiza el bloque de cargador \(SLB\).|  
  
## Comentarios  
 La función de `__svm_skinit` es equivalente a la instrucción máquina de `SKINIT` .  Esta función es parte de un sistema de seguridad que utiliza el procesador y un Módulo de plataforma \(TPM\) segura para comprobar y cargar el software confianza denominado una seguridad kernel \(SK\).  Una máquina virtual monitor es un ejemplo de una seguridad kernel.  El sistema de seguridad comprueba los componentes de programa cargados durante el proceso de inicialización, y protege los componentes de manipulación por interrupciones, el acceso del dispositivo, u otro programa si el equipo es una versión multiprocesador.  
  
 El parámetro de `SLB` especifica la dirección física de un bloque de memoria denominado del *bloque de cargador seguro \(SLB\)* .  El SLB contiene un programa llamado el cargador seguro que establece el entorno operativo del equipo, y carga posteriormente la seguridad kernel.  
  
 Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “volumen 2 de Manual del programador de arquitectura AMD64: Programa del sistema,” número de documento 24593, revisión 3,11, en [compañía de AMD](http://go.microsoft.com/fwlink/?LinkId=23746) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__svm_skinit`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)