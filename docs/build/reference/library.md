---
title: "LIBRARY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LIBRARY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LIBRARY (instrucción de archivo .def)"
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# LIBRARY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica a LINK que cree un archivo DLL.  Al mismo tiempo, LINK crea una biblioteca de importación, a menos que se utilice un archivo .exp en la compilación.  
  
```  
LIBRARY [library][BASE=address]  
```  
  
## Comentarios  
 El argumento *library* especifica el nombre de la DLL.  También se puede utilizar la opción [\/OUT](../../build/reference/out-output-file-name.md) del vinculador para especificar el nombre de la DLL resultante.  
  
 El argumento BASE\=*dirección* establece la dirección base utilizada por el sistema operativo para cargar la DLL.  Este argumento permite reemplazar la ubicación predeterminada de la DLL \(0x10000000\).  Vea la descripción de la opción [\/BASE](../../build/reference/base-base-address.md) correspondiente para obtener más información sobre direcciones base.  
  
 Acuérdese de utilizar la opción [\/DLL](../../build/reference/dll-build-a-dll.md) del vinculador cuando compile una DLL.  
  
## Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)