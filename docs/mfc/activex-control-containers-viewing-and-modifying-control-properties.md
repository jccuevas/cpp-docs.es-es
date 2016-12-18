---
title: "Contenedores de controles ActiveX: Ver y modificar propiedades de los controles | Microsoft Docs"
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
  - "contenedores de controles ActiveX [C++], ver y modificar las propiedades"
  - "controles ActiveX [C++], propiedades"
  - "controles [MFC], propiedades"
  - "propiedades [MFC], ver y modificar"
  - "editores de recursos, ver y modificar controles ActiveX"
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores de controles ActiveX: Ver y modificar propiedades de los controles
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando inserte un control ActiveX en un proyecto, es útil ver y cambiar las propiedades admitidas por el control ActiveX.  En este artículo se explica cómo utilizar el editor de recursos de Visual C\+\+ para ello.  
  
 Si la aplicación contenedora de controles ActiveX utiliza controles incrustados, puede ver y modificar las propiedades del control mientras en el editor de recursos.  También puede utilizar el editor de recursos para establecer valores de propiedad en tiempo de diseño.  El editor de recursos a guarda automáticamente estos valores en el archivo de recursos del proyecto.  Cualquier instancia del control tendrá sus propiedades inicializado con estos valores.  
  
 Este procedimiento supone que ha insertado un control en el proyecto.  Para obtener información, vea [Contenedores de controles ActiveX: Insertar un Control Into una aplicación contenedora de Control](../mfc/inserting-a-control-into-a-control-container-application.md).  
  
 El primer paso para ver las propiedades del control es agregar una instancia del control a la plantilla de cuadro de diálogo del proyecto.  
  
### Para ver las propiedades de un control  
  
1.  En la vista de recursos, abra la carpeta de **Cuadro de diálogo** .  
  
2.  Abra la plantilla principal del cuadro de diálogo.  
  
3.  Inserte un control ActiveX mediante el cuadro de diálogo **Insertar control ActiveX** .  Para obtener más información, vea [Controles ActiveX de vista y a un cuadro de diálogo](../mfc/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
4.  Seleccione el control ActiveX en el cuadro de diálogo.  
  
5.  De la ventana Propiedades, haga clic en el botón de **Propiedades** .  
  
 Use el cuadro de diálogo **Propiedades** para modificar y probar nuevas propiedades inmediatamente.  
  
## Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)