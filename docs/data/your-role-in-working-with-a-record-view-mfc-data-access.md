---
title: Rol del programador al utilizar una vista de registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
ms.openlocfilehash: c5c35208f654cff90e3cdf87e697e654bdfbe307
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153338"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Rol del programador al utilizar una vista de registros (acceso a datos MFC)

La siguiente tabla muestra qué se debe hacer normalmente para trabajar con una vista de registros y qué tareas realiza el marco de trabajo.

### <a name="working-with-a-record-view-you-and-the-framework"></a>Trabajar con una vista de registros: Usted y el marco de trabajo

|El programador|El marco de trabajo|
|---------|-------------------|
|Utiliza el editor de cuadros de diálogo de Visual C++ para diseñar el formulario.|Crea un recurso de plantilla de cuadro de diálogo con controles.|
|Use la [MFC Application Wizard](../mfc/reference/database-support-mfc-application-wizard.md) para crear las clases derivadas de [CRecordView](../mfc/reference/crecordview-class.md) y [CRecordset](../mfc/reference/crecordset-class.md).|Escribe las clases.|
|Asigna controles de vista de registros a miembros de datos de campo de conjuntos de registros.|Proporciona DDX entre los controles y los campos de conjuntos de registros.|
||Proporciona el valor predeterminado para los controladores de comandos **mover primero**, **Mover último**, **Mover siguiente**, y **mover anterior** comandos de menús o barra de herramientas botones.|
||Actualiza los cambios en el origen de datos.|
|[Opcional] Escribe código para rellenar cuadros de lista, cuadros combinados u otros controles con datos de otro conjunto de registros.||
|[Opcional] Escribe código para las validaciones especiales.||
|[Opcional] Escribe código para agregar o eliminar registros.||

La programación basada en formularios es solo una forma de trabajar con una base de datos. Para obtener información acerca de las aplicaciones que usan cualquier otra interfaz de usuario, o ninguna interfaz de usuario, consulte [MFC: Uso de las clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md) y [MFC: Uso de clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md). Enfoques alternativos para mostrar los registros de base de datos, vea clases [CListView](../mfc/reference/clistview-class.md) y [CTreeView](../mfc/reference/ctreeview-class.md).

## <a name="see-also"></a>Vea también

[Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)