---
title: Secuencia de operaciones para crear aplicaciones de base de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cbe18e9733388cc6e43f6ca3de520596c713b783
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381334"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Secuencia de operaciones para crear aplicaciones de base de datos
En la tabla siguiente se muestra su rol y trabajo del marco de escritura de aplicaciones de base de datos.  
  
> [!NOTE]
>  El entorno de Visual C++ y los asistentes no admiten DAO (aunque las clases DAO están incluidas y puede seguir usándolos). Microsoft recomienda utilizar ODBC para nuevos proyectos MFC. Solo debería utilizar DAO para mantener las aplicaciones existentes.  
  
### <a name="creating-database-applications"></a>Creación de aplicaciones de base de datos  
  
|Tarea|Lo hace|El marco de trabajo|  
|----------|------------|------------------------|  
|Decida si desea utilizar las clases DAO u ODBC de MFC.|Utilizar ODBC para nuevos proyectos MFC. Usar DAO para mantener las aplicaciones existentes. Para obtener información general, vea el artículo [programación del acceso a datos](../data/data-access-programming-mfc-atl.md).|El marco de trabajo proporciona clases que admiten el acceso de la base de datos.|  
|Cree la aplicación esquema con opciones de base de datos.|Ejecute al Asistente para aplicaciones MFC. Seleccione opciones en la página de soporte técnico de la base de datos. Si elige una opción que crea una vista de registros, especifique también:<br /><br /> : Nombres o nombre de origen y la tabla de datos<br />-Nombre o los nombres de consulta.|El Asistente para aplicaciones MFC crea archivos y especifica que incluyen las necesarias. Según las opciones que especifique, los archivos pueden incluir una clase de conjunto de registros.|  
|Diseñar un formulario de la base de datos o formularios.|Utilice el editor de cuadro de diálogo de Visual C++ para colocar controles en los recursos de plantilla de cuadro de diálogo para las clases de vista de registros.|El Asistente para aplicaciones MFC crea un recurso de plantilla de cuadro de diálogo vacío para rellenar de.|  
|Crear clases de vista y el conjunto de registros de registros adicionales según sea necesario.|Utilice la vista de clases para crear las clases y el cuadro de diálogo editor para diseñar las vistas.|Vista de clases crea archivos adicionales para las clases nuevas.|  
|Crear objetos de conjunto de registros según sea necesario en el código. Utilice cada conjunto de registros para manipular registros...|Los conjuntos de registros se basan en las clases derivadas de [CRecordset](../mfc/reference/crecordset-class.md) con los asistentes.|ODBC utiliza el intercambio de campos de registros (RFX) para intercambiar datos entre la base de datos y los miembros de datos de campo del conjunto de registros. Si está utilizando una vista de registros, intercambio de datos de cuadros de diálogo (DDX) intercambia datos entre el conjunto de registros y los controles en la vista de registros.|  
|.. .o crear explícito [CDatabase](../mfc/reference/cdatabase-class.md) en el código por cada base de datos que desea abrir.|Basar los objetos de conjunto de registros en los objetos de base de datos.|El objeto de base de datos proporciona una interfaz para el origen de datos.|  
|Enlazar dinámicamente columnas de datos para el conjunto de registros.|En ODBC, agregue código a la clase de conjunto de registros derivada para administrar el enlace. Vea el artículo [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||  
  
## <a name="see-also"></a>Vea también  
 [Compilar en el marco de trabajo](../mfc/building-on-the-framework.md)   
 [Secuencia de operaciones para compilar aplicaciones MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Secuencia de operaciones para crear aplicaciones OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Secuencia de operaciones para crear controles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
