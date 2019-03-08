---
title: Secuencia de operaciones para crear controles ActiveX
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
ms.openlocfilehash: fdfa2333681c988c0e7bceab01eab24b118f1a5a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275992"
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>Secuencia de operaciones para crear controles ActiveX

En la tabla siguiente se muestra su rol y roles de .NET framework en la creación de controles ActiveX (anteriormente conocidos como controles OLE).

### <a name="creating-activex-controls"></a>Creación de controles ActiveX

|Tarea|Lo hace|El marco de trabajo|
|----------|------------|------------------------|
|Crear un control ActiveX.|Ejecute el Asistente para controles de ActiveX de MFC para crear el control. Especifique las opciones que desee en las páginas de opciones. Las opciones incluyen el tipo y el nombre del control en el proyecto, licencias, creación de subclases y un método de cuadro acerca de.|El Asistente para controles de ActiveX de MFC crea los archivos para un control ActiveX con funcionalidad básica, incluidos los archivos de origen para la aplicación, control y página de propiedades o páginas; un archivo de recursos; un archivo de proyecto y otros, todos adaptados a sus especificaciones.|
|Vea lo que el control y el Asistente para controles ActiveX que se ofrecen sin agregar una línea de su propio código.|Compilar el control ActiveX y probarlo con Internet Explorer o el [ejemplo TSTCON](../visual-cpp-samples.md).|El control de ejecución tiene la capacidad de cambiar de tamaño y mover. También tiene un **cuadro acerca de** método (si se eligen) que se puede invocar.|
|Implemente los métodos y propiedades del control.|Implemente los métodos específicos de control de las propiedades mediante la adición de funciones miembro para proporcionar una interfaz expuesta a los datos del control. Agregue variables miembro para almacenar estructuras de datos y usar controladores de eventos para desencadenar eventos al determinar.|El marco de trabajo ya ha definido una asignación para admitir métodos, permitiéndole centrarse en cómo se implementan las propiedades y métodos, propiedades y eventos del control. Se puede ver la página de propiedades predeterminada y se proporciona un método de cuadro acerca de forma predeterminada.|
|Construir el control de la página de propiedades o las páginas.|Use los editores de recursos de Visual C++ para editar visualmente la interfaz de página de propiedades del control:<br /><br />-Crear páginas de propiedades adicionales.<br />-Crear y editar mapas de bits, iconos y cursores.<br /><br /> También puede probar las páginas de propiedades en el editor de cuadro de diálogo.|El archivo de recursos predeterminado creado por el Asistente para aplicaciones MFC proporciona muchos de los recursos que necesita. Visual C++ permite editar los recursos existentes y agregar nuevos recursos fácilmente y visualmente.|
|Probar las propiedades, métodos y eventos del control.|Volver a generar el control y usar el contenedor de prueba para comprobar que los controladores funcionan correctamente.|Puede invocar los métodos del control y manipulan sus propiedades a través de la interfaz de la página de propiedad o contenedor de prueba. Además, puede utilizar Test Container para registrar eventos desencadenados desde el control y las notificaciones recibidas por el contenedor del control.|

## <a name="see-also"></a>Vea también

[Compilación en el marco](../mfc/building-on-the-framework.md)<br/>
[Secuencia de operaciones para compilar aplicaciones MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Secuencia de operaciones para crear aplicaciones OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Secuencia de operaciones para crear aplicaciones de base de datos](../mfc/sequence-of-operations-for-creating-database-applications.md)
