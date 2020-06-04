---
title: Secuencia de operaciones para crear aplicaciones OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
ms.openlocfilehash: b7fa989d1a3b799cf6b427e27142d4479be900bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308191"
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>Secuencia de operaciones para crear aplicaciones OLE

En la tabla siguiente se muestra su rol y roles de .NET framework en la creación de vinculación e incrustación de las aplicaciones OLE. Estos representan las opciones disponibles en lugar de una secuencia de pasos para realizar.

### <a name="creating-ole-applications"></a>Crear aplicaciones OLE

|Tarea|Lo hace|El marco de trabajo|
|----------|------------|------------------------|
|Crear un componente COM.|Ejecute al Asistente para aplicaciones MFC. Elija **servidor completo** o **miniservidor** en el **compatibilidad con documentos compuestos** ficha.|El marco de trabajo genera una aplicación esqueleto con capacidad para componentes COM. Toda la capacidad de COM se pueden transferir a la aplicación existente con una pequeña modificación.|
|Cree una aplicación de contenedor desde el principio.|Ejecute al Asistente para aplicaciones MFC. Elija **contenedor** en el **compatibilidad con documentos compuestos** ficha. Vista de clases, vaya al editor de código fuente. Rellene el código para las funciones de controlador COM.|El marco de trabajo genera una aplicación esqueleto que puede insertar los objetos COM creados por las aplicaciones COM componente (servidor).|
|Crear una aplicación que admite la automatización desde cero.|Ejecute al Asistente para aplicaciones MFC. Elija **automatización** desde el **características avanzadas** ficha. Utilice la vista de clases para exponer métodos y propiedades de la aplicación para la automatización.|El marco de trabajo genera una aplicación de esqueleto que se puede activar y automatizada por otras aplicaciones.|

## <a name="see-also"></a>Vea también

[Compilación en el marco](../mfc/building-on-the-framework.md)<br/>
[Secuencia de operaciones para compilar aplicaciones MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Secuencia de operaciones para crear controles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)<br/>
[Secuencia de operaciones para crear aplicaciones de base de datos](../mfc/sequence-of-operations-for-creating-database-applications.md)
