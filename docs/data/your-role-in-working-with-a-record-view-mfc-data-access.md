---
title: El rol cuando se trabaja con una vista de registros (acceso a datos MFC) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e7a9d3fa7e828467e73c77736fb5643baf19660f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Rol del programador al utilizar una vista de registros (acceso a datos MFC)
La siguiente tabla muestra qué se debe hacer normalmente para trabajar con una vista de registros y qué tareas realiza el marco de trabajo.  
  
### <a name="working-with-a-record-view-you-and-the-framework"></a>Trabajar con una vista de registros: el programador y el marco de trabajo  
  
|El programador|El marco de trabajo|  
|---------|-------------------|  
|Utiliza el editor de cuadros de diálogo de Visual C++ para diseñar el formulario.|Crea un recurso de plantilla de cuadro de diálogo con controles.|  
|Use la [Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md) para crear clases derivadas de [CRecordView](../mfc/reference/crecordview-class.md) y [CRecordset](../mfc/reference/crecordset-class.md).|Escribe las clases.|  
|Asigna controles de vista de registros a miembros de datos de campo de conjuntos de registros.|Proporciona DDX entre los controles y los campos de conjuntos de registros.|  
||Proporciona predeterminada de controladores de comandos para **mover primero**, **Mover último**, **Mover siguiente**, y **mover anterior** comandos de menús o barra de herramientas botones.|  
||Actualiza los cambios en el origen de datos.|  
|[Opcional] Escribe código para rellenar cuadros de lista, cuadros combinados u otros controles con datos de otro conjunto de registros.||  
|[Opcional] Escribe código para las validaciones especiales.||  
|[Opcional] Escribe código para agregar o eliminar registros.||  
  
 La programación basada en formularios es solo una forma de trabajar con una base de datos. Para obtener información acerca de las aplicaciones con otra interfaz de usuario o sin interfaz de usuario, consulte [MFC: utilizar clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md) y [MFC: utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md). Para conocer otras maneras de mostrar registros de base de datos, vea clases [CListView](../mfc/reference/clistview-class.md) y [CTreeView](../mfc/reference/ctreeview-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)   
 [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)