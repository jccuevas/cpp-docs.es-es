---
title: "STUB | Microsoft Docs"
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
  - "STUB"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STUB (instrucción de archivo .def)"
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# STUB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando se utiliza en un archivo de definición de módulo que compila un controlador de dispositivo virtual \(VxD\), permite especificar un nombre de archivo que contiene una estructura IMAGE\_DOS\_HEADER \(definida en WINNT.H\) que se utilizará en el controlador de dispositivo virtual \(VxD\), en vez de en el encabezado predeterminado.  
  
```  
STUB:filename  
```  
  
## Comentarios  
 Un modo equivalente de especificar *filename* es con la opción [\/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) del vinculador.  
  
 STUB es válido en un archivo de definición de módulo cuando se desea compilar un VxD.  
  
## Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)