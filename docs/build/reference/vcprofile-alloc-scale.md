---
title: "VCPROFILE_ALLOC_SCALE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VCPROFILE_ALLOC_SCALE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VCPROFILE_ALLOC_SCALE (variable de entorno)"
ms.assetid: 5cb5ce27-f9b8-489b-b46c-d6e9bcab2d34
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# VCPROFILE_ALLOC_SCALE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Modifica la cantidad de memoria asignada para que pueda contener los datos del perfil.  
  
## Sintaxis  
  
```  
VCPROFILE_ALLOC_SCALE=scale_value  
```  
  
#### Parámetros  
 `scale_value`  
 El valor de escala para la cantidad de memoria deseada para ejecutar los escenarios de prueba.  El valor predeterminado es 1.  
  
## Comentarios  
 En casos raros, no habrá bastante memoria disponible para admitir los datos de perfil recopilados al ejecutar los escenarios de prueba.  En esos casos, puede aumentar la cantidad de memoria con `VCPROFILE_ALLOC_SCALE`.  
  
 Si recibe un mensaje de error durante una ejecución de prueba que indica que la memoria es insuficiente, asigne un valor mayor a `VCPROFILE_ALLOC_SCALE`, hasta que las ejecuciones de prueba se realicen sin errores de memoria insuficiente.  
  
## Ejemplo  
  
```  
set VCPROFILE_ALLOC_SCALE=2  
```  
  
## Vea también  
 [Variables de entrono para las optimizaciones guiadas por perfiles](../../build/reference/environment-variables-for-profile-guided-optimizations.md)