---
title: "Clases de cuadros de di&#225;logo comunes OLE | Microsoft Docs"
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
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX (clases) [C++]"
  - "clases de cuadros de diálogo comunes"
  - "clases de cuadro de diálogo [C++], OLE"
  - "clases de cuadros de diálogo comunes OLE [C++]"
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de cuadros de di&#225;logo comunes OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases controlan tareas VIEJAS comunes implementando varios cuadros de diálogo de OLE estándar.  También proporcionan una interfaz de usuario coherente para la funcionalidad OLE.  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 Utiliza el marco para contener las implementaciones comunes para todos los cuadros de diálogo de OLE.  Todas las clases de cuadro de diálogo en la categoría de la interfaz de usuario se derivan de esta clase base.  `COleDialog` no se puede utilizar directamente.  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 Muestra el cuadro de diálogo del objeto INSERT, la interfaz de usuario estándar para insertar los nuevos elementos vinculados o insertados OLE.  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 Muestra el cuadro de diálogo de pegar especial, la interfaz de usuario estándar para implementar el comando de pegar especial de edición.  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 Muestra el cuadro de diálogo de los vínculos de edición, la interfaz de usuario estándar para la información de modificación sobre elementos vinculados.  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 Muestra el cuadro de diálogo del icono de cambio, la interfaz de usuario estándar para cambiar el icono asociado a un elemento incrustado o vinculado OLE.  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 Muestra el cuadro de diálogo convert, la interfaz de usuario estándar para convertir elementos de OLE a partir de un tipo a otro.  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 Encapsula el cuadro de diálogo Propiedades OLE común de Windows.  Los cuadros de diálogo de Propiedades de OLE comunes proporcionan una manera fácil de mostrar y modificar las propiedades de un elemento OLE de una manera coherente con los estándares de Windows.  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 Muestra el cuadro de diálogo de la actualización, la interfaz de usuario estándar para actualizar todos los vínculos en un documento.  El cuadro de diálogo contiene un indicador de progreso para indicar cómo el cierre el procedimiento de actualización está completamente.  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 Muestra el cuadro de diálogo del origen del cambio, la interfaz de usuario estándar para cambiar el destino o el origen de un vínculo.  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 Muestra el Servidor No disponibles y los cuadros de diálogo No Responder de Servidor, la interfaz de usuario estándar para administrar las llamadas a las aplicaciones No disponibles.  Mostrado normalmente automáticamente por la implementación de `COleMessageFilter` .  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)