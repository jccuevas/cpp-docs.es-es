---
title: "Crear una funci&#243;n auxiliar personalizada | Microsoft Docs"
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
  - "funciones auxiliares"
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Crear una funci&#243;n auxiliar personalizada
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se puede proporcionar una versión propia de la rutina para realizar un procesamiento específico basado en los nombres de las DLL o las importaciones.  Hay dos métodos para ello: codificar una versión propia, basada posiblemente en el código proporcionado, o simplemente enlazar la versión proporcionada mediante los enlaces de notificación detallados anteriormente.  
  
 Codificar una versión propia  
 Este método es bastante sencillo porque se puede utilizar básicamente el código proporcionado como guía para la versión nueva.  Por supuesto, debe seguir las convenciones de llamada y, si vuelve a los thunks generados por el vinculador, debe devolver un puntero a función apropiado.  Una vez en el código, se puede hacer lo que se desee para llevar a cabo la llamada o salir de ella.  
  
 Utilizar el enlace de notificación de procesamiento inicial  
 Es probable que lo más fácil sea proporcionar simplemente un puntero nuevo a una función de enlace de notificación proporcionado por el usuario que reciba los mismos valores que la rutina auxiliar predeterminada en la notificación dliStartProcessing.  En ese momento, la función de enlace se puede convertir básicamente en la nueva función auxiliar, ya que un valor correcto devuelto a la rutina auxiliar predeterminada omitirá cualquier procesamiento posterior en dicha rutina.  
  
## Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)