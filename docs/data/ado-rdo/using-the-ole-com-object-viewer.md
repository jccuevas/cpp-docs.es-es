---
title: "Utilizar el Visor de objetos OLE y COM | Microsoft Docs"
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
  - "controles ActiveX [C++], ver interfaces internas"
  - "visor de objetos para objetos de automatización"
  - "visor de objetos OLE/COM"
ms.assetid: a3359e31-2869-451d-9571-129b4e8b41f0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar el Visor de objetos OLE y COM
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede utilizar el visor de objetos OLE y COM para ver las interfaces de un control.  
  
### Para utilizar el Visor de objetos OLE y COM  
  
1.  Inicie el visor de objetos OLE y COM \(oleview.exe\), que se encuentra en la carpeta del \\Windows Kits\\8.0\\bin\\x86\\ de los archivos de \\Program \(x86\).  
  
2.  En la categoría de **Clases de objeto, Agrupada de componente** en el visor, abra la carpeta de **Objetos de automatización** para ver los objetos registrados de automatización.  
  
3.  Seleccione uno de los controles.  Varias fichas aparecen en el panel derecho; las interfaces implementadas por el control se muestran en la ficha de **Registro** .  
  
    -   Si abre el menú contextual para un control en el panel izquierdo y después elija **Información de tipo de vista**, el visor de ITypeInfo muestra un archivo .odl o .idl reconstruido.  
  
    -   Si expande el nodo del control en el panel izquierdo, una lista de interfaces del objeto se muestra.  Si selecciona una interfaz, la entrada del Registro se muestra en el panel derecho.  
  
    -   Si abre el menú contextual para una interfaz y después elija **Visualización**, el visor de objetos OLE y COM muestra un cuadro de diálogo que muestra el GUID de la interfaz y una opción para ver información de biblioteca de tipos, si está disponible.  La selección de **Información de tipo de vista** muestra una parte de un archivo recompilado .idl específicos de la interfaz del visor de ITypeInfo.  
  
    -   En el visor de ITypeInfo, puede seleccionar un miembro de interfaz en la vista de árbol para mostrar las firmas de método de descriptor de acceso en el panel derecho.  
  
## Vea también  
 [Utilizar controles ActiveX](../../data/ado-rdo/using-activex-controls.md)