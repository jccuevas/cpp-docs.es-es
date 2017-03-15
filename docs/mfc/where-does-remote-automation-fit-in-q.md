---
title: "&#191;D&#243;nde encaja la automatizaci&#243;n remota? | Microsoft Docs"
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
  - "automatización remota, DCOM"
ms.assetid: 4c4c8176-cfc0-44f7-bc87-b690f069ad2f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#191;D&#243;nde encaja la automatizaci&#243;n remota?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DCOM se libera en 1996 y está disponible con plataformas de 32 bits y de 64 bits de.  El equipo de Visual Basic en Microsoft ha visto siempre Visual Basic como mediante automatización para permitir que los componentes comunicar.  La falta de una versión enrutada restringidos gravemente el uso de estas características en los entornos empresariales, por lo que el equipo que desarrollaba Visual Basic 4.0 Enterprise Edition decidió investigar la creación de su propio conjunto de componentes de comunicación remota para las partes de automatización OLE y COM.  Claramente, un objetivo importante es asegurarse de que el resultado se admiten y se podría reemplazar DCOM cuando estaba disponible.  A continuación continuaron para implementar la automatización remota \(RA\) para plataformas de 16 bits y de 32 bits de Windows.  
  
 Automatización remota no está asociado a ningún idioma específico, pero hasta el lanzamiento de Visual C\+\+ 4.2 Enterprise Edition, se envió sólo con Visual Basic 4.0.  Tenga en cuenta que la automatización remota está incluida totalmente DCOM.  Si tiene la oportunidad de utilizar DCOM en lugar de automatización remota en las aplicaciones, debe hacerlo.  Sin embargo, hay escenarios donde es más adecuada la automatización remota:  
  
-   Siempre que tenga clientes de 16 bits.  
  
-   Si la organización no ha desarrollado una versión DCOM\- habilitada de Windows NT o Windows 95 todavía.  
  
-   Si está actualizando un conjunto de aplicaciones existente que usa la automatización remota para utilizar componentes de C\+\+ en lugar de uno o más componentes de Visual Basic.  
  
 No es necesario diferencia entre los programas creados para utilizar la automatización remota y los creados para utilizar la automatización sobre DCOM, y las utilidades de configuración crean muy sencillo cambiar la operación entre la automatización remota y DCOM.  Por consiguiente, no es difícil actualizar una aplicación de automatización remota a DCOM una vez que la infraestructura existe.  
  
## Vea también  
 [¿Qué proporciona la automatización remota?](../mfc/what-does-remote-automation-provide-q.md)   
 [Historial de DCOM](../mfc/history-of-dcom.md)