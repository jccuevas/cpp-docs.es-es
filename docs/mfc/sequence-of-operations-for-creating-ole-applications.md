---
title: "Secuencia de operaciones para crear aplicaciones OLE | Microsoft Docs"
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
  - "aplicaciones [OLE]"
  - "aplicaciones [OLE], crear"
  - "aplicaciones OLE [C++]"
  - "aplicaciones OLE [C++], crear"
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Secuencia de operaciones para crear aplicaciones OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente muestra el rol y el rol de marco en crear OLE que vincula y que inserta aplicaciones.  Éstos representan las opciones disponibles en lugar de una secuencia de pasos para realizar.  
  
### Crear aplicaciones OLE  
  
|Tarea|Hace|Hace el marco|  
|-----------|----------|-------------------|  
|Cree un componente COM.|Ejecute el asistente para aplicaciones MFC.  Elija **Full\-server** o **Mini\-server** en la pestaña de **Compatib. doc. compuestos** .|El marco genera una aplicación esqueleto con la capacidad del componente COM habilitada.  Toda la funcionalidad COM se puede transferir a la aplicación existente con sólo la modificación leve.|  
|Cree una aplicación contenedora desde cero.|Ejecute el asistente para aplicaciones MFC.  Elija **Contenedor** en la pestaña de **Compatib. doc. compuestos** .  Mediante la vista de clases, vaya al editor de código fuente.  Complete el código para las funciones COM de controlador.|El marco genera una aplicación esqueleto que puede insertar los objetos COM creados con aplicaciones de componentes COM \(servidor\).|  
|Cree una aplicación que admita automatización desde cero.|Ejecute el asistente para aplicaciones MFC.  Elija **Automatización** desde la ficha de **Características avanzadas** .  Utilice la vista de clases para exponer métodos y propiedades de la aplicación para la automatización.|El marco genera una aplicación esqueleto que se pueda activar y automatizar por otras aplicaciones.|  
  
## Vea también  
 [Compilar en el marco](../mfc/building-on-the-framework.md)   
 [Secuencia de operaciones para compilar aplicaciones MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Secuencia de operaciones para crear controles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Secuencia de operaciones para crear aplicaciones de base de datos](../mfc/sequence-of-operations-for-creating-database-applications.md)