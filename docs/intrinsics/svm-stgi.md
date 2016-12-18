---
title: "__svm_stgi | Microsoft Docs"
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
  - "__svm_stgi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__svm_stgi (función instrínseca)"
  - "STGI (instrucción)"
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_stgi
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Establece la marca global de la interrupción.  
  
## Sintaxis  
  
```  
void __svm_stgi(void);  
```  
  
## Comentarios  
 La función de `__svm_stgi` es equivalente a la instrucción máquina de `STGI` .  La marca global de la interrupción determina si el microprocesador omite, posponer, o controla las interrupciones debido a los eventos como una finalización de E\/S, una alerta de temperatura de hardware, o una excepción de depuración.  
  
 Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “volumen 2 de Manual del programador de arquitectura AMD64: Programa del sistema,” número de documento 24593, revisión 3,11, en [compañía de AMD](http://go.microsoft.com/fwlink/?LinkId=23746) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__svm_stgi`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_clgi](../intrinsics/svm-clgi.md)