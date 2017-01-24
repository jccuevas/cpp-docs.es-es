---
title: "Mapas de env&#237;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macros de mapa de envíos"
  - "mapas de envío"
  - "macros de mapas de envíos"
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
caps.latest.revision: 14
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mapas de env&#237;o
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Automatización OLE proporciona maneras de llamar a métodos y tener acceso a propiedades en varias aplicaciones.  El mecanismo proporcionado por la biblioteca Microsoft Foundation Class para enviar estas solicitudes es “mapa send,” que señala los nombres internos y externos de funciones y propiedades del objeto, así como los tipos de datos de las propiedades propias y de argumentos de función.  
  
### Mapas de envío  
  
|||  
|-|-|  
|[DECLARE\_DISPATCH\_MAP](../Topic/DECLARE_DISPATCH_MAP.md)|Declara que un mapa de envío se utilizará para exponer los métodos y las propiedades de una clase \(se utiliza en la declaración de clase\).|  
|[BEGIN\_DISPATCH\_MAP](../Topic/BEGIN_DISPATCH_MAP.md)|Inicia la definición de un mapa de envío.|  
|[END\_DISPATCH\_MAP](../Topic/END_DISPATCH_MAP.md)|Finaliza la definición de un mapa de envío.|  
|[DISP\_FUNCTION](../Topic/DISP_FUNCTION.md)|Utilizado en un mapa de envío para definir una función de automatización OLE.|  
|[DISP\_PROPERTY](../Topic/DISP_PROPERTY.md)|Define una propiedad de automatización OLE.|  
|[DISP\_PROPERTY\_EX](../Topic/DISP_PROPERTY_EX.md)|Define una propiedad de automatización OLE y nombres el obtener y el conjunto funcionan.|  
|[DISP\_PROPERTY\_NOTIFY](../Topic/DISP_PROPERTY_NOTIFY.md)|Define una propiedad de automatización OLE con la notificación.|  
|[DISP\_PROPERTY\_PARAM](../Topic/DISP_PROPERTY_PARAM.md)|Define una propiedad de automatización OLE que toma parámetros y funcionan los nombres las instrucciones get y set.|  
|[DISP\_DEFVALUE](../Topic/DISP_DEFVALUE.md)|Crea una propiedad existente el valor predeterminado de un objeto.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)