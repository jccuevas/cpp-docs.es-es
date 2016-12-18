---
title: "Volcar importaciones de carga retrasada | Microsoft Docs"
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
  - "importaciones de carga retrasada"
  - "importaciones de carga retrasada, volcar"
  - "importaciones (de carga retrasada)"
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Volcar importaciones de carga retrasada
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las importaciones de carga retrasada se pueden volcar mediante [dumpbin \/imports](../../build/reference/imports-dumpbin.md) y mostrarse con información ligeramente distinta de la de las importaciones estándar.  Permanecen apartadas en su propia sección del volcado \/imports y se etiquetan explícitamente como importaciones de carga retrasada.  Se anota cualquier información de descarga presente en la imagen.  Si existe información de enlace, se anota la marca de fecha y hora de la DLL de destino junto con las direcciones de enlace de las importaciones.  
  
## Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)