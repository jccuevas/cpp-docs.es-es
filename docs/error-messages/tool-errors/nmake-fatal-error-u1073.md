---
title: "Error grave de NMAKE U1073 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1073"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1073"
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error grave de NMAKE U1073
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se sabe cómo hacer 'nombrededestino'  
  
 No existe el destino especificado y no se pueden ejecutar comandos ni aplicar reglas de inferencia.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Compruebe si se ha escrito correctamente el nombre de destino.  
  
2.  Si *nombrededestino* es un pseudodestino, especifíquelo como un destino en otro bloque de descripciones.  
  
3.  Si *nombrededestino* es una llamada de macro, asegúrese de que no se expande a una cadena nula.