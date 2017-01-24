---
title: "Generadores de clases y licencias | Microsoft Docs"
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
  - "vc.mfc.macros.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generadores de clases, y otorgar licencias"
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
caps.latest.revision: 13
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Generadores de clases y licencias
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para crear una instancia de controles activex, una aplicación contenedora llama a una función miembro de generador de clases de control.  Dado que el control es un objeto OLE real, el generador de la clase es responsable de crear instancias del control.  Cada clase de controles activex debe tener un generador de clases.  
  
 Otra característica importante de los controles OLE es la capacidad de aplicar una licencia.  ControlWizard permite incorporar la autorización durante la creación del proyecto de control.  Para obtener más información sobre el control que autoriza, vea el artículo [Controles ActiveX: Autorización de un control ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
 La tabla siguiente se muestran varias macros y funciones que se usan para declarar e implementar el generador de la clase de control y de licencia del control.  
  
### Generadores y Licencias de clase  
  
|||  
|-|-|  
|[DECLARE\_OLECREATE\_EX](../Topic/DECLARE_OLECREATE_EX.md)|Declara el generador de clases para un control OLE o una página de propiedades.|  
|[IMPLEMENT\_OLECREATE\_EX](../Topic/IMPLEMENT_OLECREATE_EX.md)|Implementa la función de `GetClassID` de control y declara una instancia de generador de clases.|  
|[BEGIN\_OLEFACTORY](../Topic/BEGIN_OLEFACTORY.md)|Comience la declaración de cualquier función de autorización.|  
|[END\_OLEFACTORY](../Topic/END_OLEFACTORY.md)|Finaliza la declaración de cualquier función de autorización.|  
|[AfxVerifyLicFile](../Topic/AfxVerifyLicFile.md)|Comprueba si un control tiene autorización para el uso en un equipo determinado.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)