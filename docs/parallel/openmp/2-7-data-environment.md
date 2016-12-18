---
title: "2.7 Data Environment | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7 Data Environment
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta sección muestra una directiva y varias cláusulas para controlar el entorno de datos durante la ejecución de las regiones paralelas, como sigue:  
  
-   Una directiva de **threadprivate** \(vea la siguiente sección\) se proporciona para que el ámbito del archivo, espacio de nombres\-ámbito, o las variables estáticas de bloque\-ámbito locales de un subproceso.  
  
-   Las cláusulas que se pueden especificar en las directivas para controlar los atributos de variables para la duración de las construcciones paralelas o la división del trabajo se describen en [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.