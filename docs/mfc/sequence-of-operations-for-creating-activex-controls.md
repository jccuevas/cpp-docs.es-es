---
title: Secuencia de operaciones para crear controles ActiveX | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: caf4c74f2263505ad5d7112021003f92c85a4b84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>Secuencia de operaciones para crear controles ActiveX
En la tabla siguiente se muestra su rol y trabajo del marco de en la creación de controles ActiveX (anteriormente conocidos como controles OLE).  
  
### <a name="creating-activex-controls"></a>Crear controles ActiveX  
  
|Tarea|Lo hace|El marco de trabajo|  
|----------|------------|------------------------|  
|Cree un marco de trabajo del control ActiveX.|Ejecute el Asistente para controles de ActiveX de MFC para crear el control. Especifique las opciones que desee en las páginas de opciones. Opciones incluyen el tipo y el nombre del control en el proyecto, licencias, subclases y un método de cuadro acerca de.|El Asistente para controles de ActiveX de MFC crea los archivos para un control ActiveX con funcionalidad básica, incluidos los archivos de origen para la aplicación, control y página de propiedades o páginas; un archivo de recursos; un archivo de proyecto; y otros usuarios, todos ellos personalizados según según sus especificaciones.|  
|Ver lo que el control y el Asistente para controles ActiveX ofrecen sin agregar una línea de su propio código.|Compilar el control ActiveX y probarlo con Internet Explorer o la [ejemplo TSTCON](../visual-cpp-samples.md).|El control de ejecución tiene la capacidad de cambiar de tamaño y mover. También tiene un **sobre cuadro** método (si elige) que se puede invocar.|  
|Implemente los métodos y propiedades del control.|Implemente los métodos específicos de control y propiedades agregando funciones miembro para proporcionar una interfaz expuesta a los datos del control. Agregue variables miembro para almacenar las estructuras de datos y usar controladores de eventos para desencadenar los eventos para determinar.|El marco de trabajo ya ha definido una asignación para admitir eventos, propiedades y métodos, dejando que pueda centrarse en cómo se implementan los métodos y propiedades del control. La página de propiedades predeterminada es visible y se proporciona un método de cuadro acerca de predeterminado.|  
|Crear página de propiedades del control o las páginas.|Utilice los editores de recursos de Visual C++ para editar visualmente la interfaz de página de propiedades del control:<br /><br /> -Crear páginas de propiedades adicionales.<br />-Crear y editar mapas de bits, iconos y cursores.<br /><br /> También puede probar las páginas de propiedades en el editor de cuadro de diálogo.|El archivo de recursos predeterminado creado por el Asistente para aplicaciones MFC proporciona muchos de los recursos que necesita. Visual C++ permite editar los recursos existentes y agregar nuevos recursos fácilmente y visualmente.|  
|Probar propiedades, métodos y eventos del control.|Vuelva a generar el control y utilice Test Container para probar que los controladores funcionan correctamente.|Puede invocar los métodos del control y manipular sus propiedades a través de la interfaz de la página de propiedades o el contenedor de prueba. Además, puede usar Test Container a seguimiento se activa desde el control de eventos y notificaciones recibidas por el contenedor del control.|  
  
## <a name="see-also"></a>Vea también  
 [Compilar en el marco de trabajo](../mfc/building-on-the-framework.md)   
 [Secuencia de operaciones para compilar aplicaciones MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Secuencia de operaciones para crear aplicaciones OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Secuencia de operaciones para crear aplicaciones de base de datos](../mfc/sequence-of-operations-for-creating-database-applications.md)

