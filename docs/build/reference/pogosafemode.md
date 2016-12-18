---
title: "PogoSafeMode | Microsoft Docs"
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
helpviewer_keywords: 
  - "PogoSafeMode"
ms.assetid: 2daeeff7-44cb-417f-90eb-6b9edf658533
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# PogoSafeMode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifique si se utilizará el modo rápido o el modo seguro para la generación de perfiles de aplicaciones.  
  
## Sintaxis  
  
```  
PogoSafeMode  
```  
  
## Comentarios  
 La optimización guiada por perfiles tiene dos posibles modos durante la fase de generación de perfiles: modo rápido y modo seguro.  Al generar perfiles en modo rápido, utiliza la instrucción **INC** para aumentar los contadores de datos.  La instrucción **INC** es más rápida pero no es segura para subprocesos.  Al generar perfiles en modo seguro, utiliza la instrucción **LOCK INC** para aumentar los contadores de datos.  La instrucción **LOCK INC** tiene la misma funcionalidad que la instrucción **INC** y es segura para subprocesos, pero es más lenta que la instrucción **INC**.  
  
 De forma predeterminada, la creación de perfiles PGO funciona en modo rápido.  Solo se requiere `PogoSafeMode` si desea utilizar el modo seguro.  
  
 Para ejecutar la generación de perfiles de PGO en modo seguro, debe utilizar la variable de entorno `PogoSafeMode` o el modificador del vinculador **\-PogoSafeMode**, dependiendo del sistema.  Si realiza la generación de perfiles en un equipo x64, debe utilizar el modificador del vinculador.  Si realiza la generación de perfiles en un equipo x86, debe definir la variable de entorno de cualquier valor antes de iniciar el proceso de optimización.  
  
## Ejemplo  
  
```  
set PogoSafeMode=1  
```  
  
## Vea también  
 [Variables de entrono para las optimizaciones guiadas por perfiles](../../build/reference/environment-variables-for-profile-guided-optimizations.md)   
 [Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)