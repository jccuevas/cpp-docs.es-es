---
title: "Error grave de NMAKE U1045 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1045"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1045"
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error grave de NMAKE U1045
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error al generar: mensaje  
  
 Error por la razón indicada en un programa o un comando llamado por NMAKE.  Cuando NMAKE llama a otro programa \(por ejemplo, el compilador o el vinculador\), puede producirse un error en la llamada, o el programa llamado puede devolver un error.  Este mensaje se utiliza para informar sobre el error.  
  
 Para corregir este problema, primero hay que determinar la causa del error.  Puede utilizar los comandos registrados por la opción [\/N](../../build/nmake-options.md) de NMAKE para comprobar la configuración del entorno y repetir las acciones realizadas por NMAKE en la línea de comandos.