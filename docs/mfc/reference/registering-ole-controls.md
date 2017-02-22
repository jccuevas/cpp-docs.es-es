---
title: "Registrar controles OLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles OLE, registrar"
  - "registrar controles OLE"
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# Registrar controles OLE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Controles OLE, como otros objetos de servidor OLE, pueden tener acceso a otras aplicaciones OLE\- con conocimiento pleno.  Esto se logra registrando la biblioteca de tipos y la clase del control.  
  
 Las siguientes funciones permiten agregar y quitar la clase del control, las páginas de propiedades, y la biblioteca de tipos en la base de datos del registro de Windows:  
  
### Registrar controles OLE  
  
|||  
|-|-|  
|[AfxOleRegisterControlClass](../Topic/AfxOleRegisterControlClass.md)|Agrega la clase del control en la base de datos de registro.|  
|[AfxOleRegisterPropertyPageClass](../Topic/AfxOleRegisterPropertyPageClass.md)|Agrega una página de propiedades del control a la base de datos de registro.|  
|[AfxOleRegisterTypeLib](../Topic/AfxOleRegisterTypeLib.md)|Agrega la biblioteca de tipos del control a la base de datos de registro.|  
|[AfxOleUnregisterClass](../Topic/AfxOleUnregisterClass.md)|Quita una clase de control o una clase de la página de propiedades de la base de datos de registro.|  
|[AfxOleUnregisterTypeLib](../Topic/AfxOleUnregisterTypeLib.md)|Quita la biblioteca de tipos de control de la base de datos de registro.|  
  
 `AfxOleRegisterTypeLib` se denomina normalmente en una implementación de DLL de control de `DllRegisterServer`.  De igual forma, `AfxOleUnregisterTypeLib` llama `DllUnregisterServer`.  `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, y `AfxOleUnregisterClass` llaman normalmente por la función miembro de `UpdateRegistry` de generador o de la página de propiedades de la clase de un control.  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)