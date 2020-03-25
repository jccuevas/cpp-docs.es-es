---
title: Rol del programador al utilizar una vista de registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
ms.openlocfilehash: 351aa2d5ce950017aa8c1b3d99c8d297a423ad9f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209006"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Rol del programador al utilizar una vista de registros (acceso a datos MFC)

La siguiente tabla muestra qué se debe hacer normalmente para trabajar con una vista de registros y qué tareas realiza el marco de trabajo.

### <a name="working-with-a-record-view-you-and-the-framework"></a>Trabajar con una vista de registros: el programador y el marco de trabajo

|Los|El marco de trabajo|
|---------|-------------------|
|Utiliza el editor de cuadros de diálogo de Visual C++ para diseñar el formulario.|Crea un recurso de plantilla de cuadro de diálogo con controles.|
|Use el [Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md) para crear clases derivadas de [CRecordView](../mfc/reference/crecordview-class.md) y [CRecordset](../mfc/reference/crecordset-class.md).|Escribe las clases.|
|Asigna controles de vista de registros a miembros de datos de campo de conjuntos de registros.|Proporciona DDX entre los controles y los campos de conjuntos de registros.|
||Proporciona controladores de comandos predeterminados para los comandos **desplace First**, **Move Last**, **Move Next**y **Move Previous** desde menús o botones de barra de herramientas.|
||Actualiza los cambios en el origen de datos.|
|[Opcional] Escribe código para rellenar cuadros de lista, cuadros combinados u otros controles con datos de otro conjunto de registros.||
|[Opcional] Escribe código para las validaciones especiales.||
|[Opcional] Escribe código para agregar o eliminar registros.||

La programación basada en formularios es solo una forma de trabajar con una base de datos. Para obtener información acerca de las aplicaciones que usan otra interfaz de usuario o no tienen interfaz de usuario, vea [MFC: usar clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md) y [MFC: usar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md). Para obtener enfoques alternativos para mostrar los registros de base de datos, vea las clases [CListView](../mfc/reference/clistview-class.md) y [CTreeView](../mfc/reference/ctreeview-class.md).

## <a name="see-also"></a>Consulte también

[Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)
