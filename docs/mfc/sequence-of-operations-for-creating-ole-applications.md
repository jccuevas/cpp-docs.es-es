---
title: Secuencia de operaciones para crear aplicaciones OLE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db3b5b9a5f4f62fa71cffa37b30a89aee41fe56f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>Secuencia de operaciones para crear aplicaciones OLE
En la tabla siguiente se muestra su rol y trabajo del marco de en la creación de vinculación e incrustación aplicaciones OLE. Estos representan opciones disponibles, en lugar de una secuencia de pasos para realizar.  
  
### <a name="creating-ole-applications"></a>Crear aplicaciones OLE  
  
|Tarea|Lo hace|El marco de trabajo|  
|----------|------------|------------------------|  
|Crear un componente COM.|Ejecute al Asistente para aplicaciones MFC. Elija **servidor completo** o **miniservidor** en el **compatibilidad con documentos compuestos** ficha.|El marco de trabajo genera una aplicación esqueleto con capacidad para componentes COM. Toda la capacidad de COM se pueden transferir a la aplicación existente con una pequeña modificación.|  
|Crear una aplicación de contenedor desde el principio.|Ejecute al Asistente para aplicaciones MFC. Elija **contenedor** en el **compatibilidad con documentos compuestos** ficha. Con la vista de clases, vaya al editor de código fuente. Rellene el código para las funciones de controlador COM.|El marco de trabajo genera una aplicación esqueleto que puede insertar los objetos COM creados por las aplicaciones de componente (servidor) de COM.|  
|Crear una aplicación que admite automatización desde el principio.|Ejecute al Asistente para aplicaciones MFC. Elija **automatización** desde el **características avanzadas** ficha. Usar la vista de clases para exponer métodos y propiedades de la aplicación para la automatización.|El marco de trabajo genera una aplicación esqueleto que puede ser activada y automatizada por otras aplicaciones.|  
  
## <a name="see-also"></a>Vea también  
 [Compilar en el marco de trabajo](../mfc/building-on-the-framework.md)   
 [Secuencia de operaciones para compilar aplicaciones MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Secuencia de operaciones para crear controles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Secuencia de operaciones para crear aplicaciones de base de datos](../mfc/sequence-of-operations-for-creating-database-applications.md)

