---
title: "Enlazar importaciones | Microsoft Docs"
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
  - "/DELAY:NOBIND (opción del vinculador)"
  - "DELAY:NOBIND (opción del vinculador)"
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Enlazar importaciones
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El comportamiento predeterminado del vinculador es crear una tabla de direcciones de importación que se pueda enlazar para la DLL de carga retrasada.  Si la DLL está enlazada, la función auxiliar intentará utilizar la información de enlace en lugar de llamar a **GetProcAddress** en cada una de las importaciones a las que se hace referencia.  Si la marca de tiempo o la dirección preferida no coinciden con las de la DLL cargada, la función auxiliar supondrá que la tabla de direcciones de importación enlazadas no está actualizada y continuará como si esta tabla no existiera.  
  
 Si no se pretende establecer en ningún momento el enlace de las importaciones del archivo DLL de carga retrasada, la especificación de [\/delay](../../build/reference/delay-delay-load-import-settings.md):nobind en la línea de comandos del vinculador evitará la generación de la tabla de direcciones de importación enlazadas y el consumo de espacio en el archivo de imagen.  
  
## Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)