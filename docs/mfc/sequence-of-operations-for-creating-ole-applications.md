---
title: Secuencia de operaciones para crear aplicaciones OLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02542f8a4eb382ff4d7a88f98163b0052be09f75
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392529"
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

