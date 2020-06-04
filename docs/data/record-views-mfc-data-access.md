---
title: Vistas de registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
ms.openlocfilehash: 31dbd92219f263c625050524279b97ef38ba9ba1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209136"
---
# <a name="record-views--mfc-data-access"></a>Vistas de registros (acceso a datos MFC)

Esta sección se aplica únicamente a las clases ODBC de MFC. Para obtener información sobre OLE DB vistas de registros, vea [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) y [usar las vistas de registros de OLE DB](../data/oledb/using-ole-db-record-views.md).

Para admitir aplicaciones de acceso a datos basadas en formularios, la biblioteca de clases proporciona la clase [CRecordView](../mfc/reference/crecordview-class.md). Una vista de registros es un objeto de vista de formulario cuyos controles se asignan directamente a los miembros de datos de campo de un objeto de [conjunto de registros](../data/odbc/recordset-odbc.md) (e indirectamente a las columnas correspondientes en el resultado de una consulta o en una tabla en el origen de datos). Como su clase base [CFormView](../mfc/reference/cformview-class.md), `CRecordView` se basa en un recurso de plantilla de cuadro de diálogo.

## <a name="form-uses"></a>Usos de los formularios

Los formularios son útiles para varias tareas de acceso a datos:

- Introducción de datos

- Realización de análisis de solo lectura de los datos

- Actualizar datos

## <a name="further-reading-about-record-views"></a>Información adicional sobre vistas de registros

El material de los temas se aplica a las clases basadas en ODBC y a las clases basadas en DAO. Use `CRecordView` para ODBC y `CDaoRecordView` para DAO.

Contenido de los temas:

- [Características de las clases de vista de registros](../data/features-of-record-view-classes-mfc-data-access.md)

- [Intercambio de datos para vistas de registros](../data/data-exchange-for-record-views-mfc-data-access.md)

- [Su rol al trabajar con una vista de registros](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)

- [Diseñar y crear una vista de registros](../data/designing-and-creating-a-record-view-mfc-data-access.md)

- [Usar una vista de registros](../data/using-a-record-view-mfc-data-access.md)

## <a name="see-also"></a>Consulte también

[Programación del acceso a datos (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)
