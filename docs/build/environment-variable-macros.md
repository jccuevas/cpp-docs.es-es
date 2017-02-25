---
title: "Macros de variables de entorno | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "variables de entorno, macros en NMAKE"
  - "macros, variable de entorno"
  - "NMAKE (programa), macros de variable de entorno"
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Macros de variables de entorno
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE hereda definiciones de macro para variables de entorno que existían antes del inicio de la sesión.  Si una variable se ha establecido en el entorno del sistema operativo, está disponible como una macro de NMAKE.  Los nombres heredados se convierten a mayúsculas.  La herencia tiene lugar antes del preprocesamiento.  La opción \/E se utiliza para que las macros heredadas de variables de entorno reemplacen las macros con el mismo nombre en el archivo MAKE.  
  
 Las macros de variables de entorno se pueden volver a definir en la sesión y esta acción cambia la variable de entorno correspondiente.  También se pueden cambiar las variables de entorno con el comando SET.  Sin embargo, el uso del comando SET para cambiar una variable de entorno en una sesión no cambia la macro correspondiente.  
  
 Por ejemplo:  
  
```  
PATH=$(PATH);\nonesuch  
  
all:  
    echo %PATH%  
```  
  
 En este ejemplo, el cambio de `PATH` modifica la variable de entorno `PATH` correspondiente; asimismo, anexa `\nonesuch` a la ruta de acceso.  
  
 Si una variable de entorno se define como una cadena que sería incorrecta en términos de sintaxis en un archivo MAKE, no se crea ninguna macro y no se genera ninguna advertencia.  Si el valor de una variable contiene un signo de moneda \($\), NMAKE lo interpreta como el comienzo de una llamada de macro.  El uso de la macro puede provocar un comportamiento inesperado.  
  
## Vea también  
 [Macros NMAKE especiales](../build/special-nmake-macros.md)