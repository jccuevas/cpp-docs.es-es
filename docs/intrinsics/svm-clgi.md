---
title: "__svm_clgi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__svm_clgi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLGI (instrucción)"
  - "__svm_clgi (función intrínseca)"
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __svm_clgi
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Borra la marca global de la interrupción.  
  
## Sintaxis  
  
```  
void __svm_clgi( void );  
```  
  
## Comentarios  
 La función de `__svm_clgi` es equivalente a la instrucción máquina de `CLGI` .  La marca global de la interrupción determina si el microprocesador omite, posponer, o controla las interrupciones debido a los eventos como una finalización de E\/S, una alerta de temperatura de hardware, o una excepción de depuración.  
  
 Esta función admite la interacción de la máquina virtual monitor de un host con un sistema operativo invitado y las aplicaciones.  Para obtener más información, busque el documento, “volumen 2 de Manual del programador de arquitectura AMD64: Programa del sistema,” número de documento 24593, revisión 3,11, en [compañía de AMD](http://go.microsoft.com/fwlink/?LinkId=23746) el sitio.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__svm_clgi`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_stgi](../intrinsics/svm-stgi.md)