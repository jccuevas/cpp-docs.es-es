---
title: "&#191;Qu&#233; proporciona la automatizaci&#243;n remota? | Microsoft Docs"
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
ms.assetid: 269ad218-e164-40ef-9b87-25fcc8ba21de
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#191;Qu&#233; proporciona la automatizaci&#243;n remota?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La automatización remota permite que los programas se invoque las implementaciones de `IDispatch` en un equipo de otro.  También admite otras interfaces requeridas por la automatización, específicamente **IEnumVARIANT** para admitir la colección.  No proporciona la capacidad de enrutar cualquier otra interfaz COM \(excepto **IUnknown**por supuesto,\) y, como la automatización regular, contiene soporte de cálculo sólo para los tipos de datos compatibles con automatización.  
  
 Este conjunto de medios permite que un programa tenga acceso a los métodos y propiedades, incluidos los que devuelven colecciones o fomentar objetos de automatización, un objeto que se ejecuta en un nodo de red accesible.  Si el equipo cliente también ejecuta el software adecuado, es posible que el servidor llame al cliente, de nuevo utilizando las funciones de automatización \(éste funciona para los clientes de 32 bits y 64 bits únicamente, y es conceptualmente similar a eventos, aunque no utilice el mismo mecanismo\).  
  
 Para que una aplicación sea operativo como servidor de automatización remota, se debe implementar como una aplicación ejecutable \(es decir, como “servidor local” en lugar de como “servidor de inproc”\).  
  
## Vea también  
 [¿Dónde encaja la automatización remota?](../mfc/where-does-remote-automation-fit-in-q.md)   
 [Historial de DCOM](../mfc/history-of-dcom.md)