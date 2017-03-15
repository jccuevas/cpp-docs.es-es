---
title: "Actualizaci&#243;n de la interfaz de usuario para vistas de registros (acceso a datos MFC) | Microsoft Docs"
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
  - "menús, actualizar cuando el contexto cambia"
  - "vistas de registros, interfaz de usuario"
  - "interfaces de usuario, actualizar"
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Actualizaci&#243;n de la interfaz de usuario para vistas de registros (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CRecordView` y `CDaoRecordView` también proporcionan controladores de actualización de la interfaz de usuario predeterminados para los comandos de navegación.  Estos controladores automatizan la habilitación y la deshabilitación de los objetos de la interfaz de usuario, como los elementos de menú y los botones de la barra de herramientas.  El asistente para aplicaciones proporciona menús estándar y, si elige la opción **Barra de herramientas acoplable** un conjunto de botones de la barra de herramientas para los comandos.  Si crea una clase de vista de registros con `CRecordView`, es posible que le interese agregar a la aplicación objetos de interfaz de usuario similares.  
  
### Cómo crear recursos de menú con el editor de menús  
  
1.  Consulte la información sobre el uso del [editor de menús](../mfc/menu-editor.md) para crear su propio menú con los mismos cuatro comandos.  
  
#### Cómo crear botones de barra de herramientas con el editor de gráficos  
  
1.  Consulte la información sobre el uso del [editor de la barra de herramientas](../mfc/toolbar-editor.md) para editar el recurso de la barra de herramientas y agregar botones de barra de herramientas a los comandos de exploración de registros.  
  
## Vea también  
 [Permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)   
 [Utilizar una vista de registros](../data/using-a-record-view-mfc-data-access.md)