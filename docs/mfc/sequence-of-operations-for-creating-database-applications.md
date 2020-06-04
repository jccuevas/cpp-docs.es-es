---
title: Secuencia de operaciones para crear aplicaciones de base de datos
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: c393269d6af108ee82786e9d59f81aad11428157
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372772"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Secuencia de operaciones para crear aplicaciones de base de datos

En la tabla siguiente se muestra el rol y el rol del marco de trabajo en la escritura de aplicaciones de base de datos.

> [!NOTE]
> El entorno y los asistentes de Visual C++ no admiten DAO (aunque las clases DAO están incluidas y todavía puede usarlas). Microsoft recomienda usar ODBC para nuevos proyectos MFC. Solo debe usar DAO para mantener las aplicaciones existentes.

### <a name="creating-database-applications"></a>Creación de aplicaciones de base de datos

|Tarea|Usted lo hace|El marco no|
|----------|------------|------------------------|
|Decida si desea utilizar las clases ODBC o DAO de MFC.|Use ODBC para nuevos proyectos MFC. Utilice DAO solo para mantener las aplicaciones existentes. Para obtener información general, consulte el artículo [Programación](../data/data-access-programming-mfc-atl.md)de acceso a datos .|El marco de trabajo proporciona clases que admiten el acceso a la base de datos.|
|Cree su aplicación de esqueleto con opciones de base de datos.|Ejecute el Asistente para aplicaciones MFC. Seleccione opciones en la página Soporte de base de datos. Si elige una opción que crea una vista de registro, especifique también:<br /><br />- Origen de datos y nombre o nombre de tabla<br />- Nombre o nombres de consulta.|El Asistente para aplicaciones MFC crea archivos y especifica las incluye necesarias. Dependiendo de las opciones que especifique, los archivos pueden incluir una clase de conjunto de registros.|
|Diseñe su formulario o formulario de base de datos.|Utilice el editor de cuadros de diálogo Visual C++ para colocar controles en los recursos de plantilla de cuadro de diálogo para las clases de vista de registros.|El Asistente para aplicaciones MFC crea un recurso de plantilla de cuadro de diálogo vacío para que lo rellene.|
|Cree clases de conjunto de registros y vista de registros adicionales según sea necesario.|Utilice la vista de clases para crear las clases y el editor de cuadros de diálogo para diseñar las vistas.|La vista de clases crea archivos adicionales para las nuevas clases.|
|Cree objetos de conjunto de registros según sea necesario en el código. Utilice cada conjunto de registros para manipular registros...|Los conjuntos de registros se basan en las clases derivadas de [CRecordset](../mfc/reference/crecordset-class.md) con los asistentes.|ODBC utiliza el intercambio de campos de registros (RFX) para intercambiar datos entre la base de datos y los miembros de datos de campo del conjunto de registros. Si utiliza una vista de registros, el intercambio de datos de cuadro de diálogo (DDX) intercambia datos entre el conjunto de registros y los controles de la vista de registros.|
|... o cree una [CDatabase](../mfc/reference/cdatabase-class.md) explícita en el código para cada base de datos que desee abrir.|Base los objetos de conjunto de registros en los objetos de base de datos.|El objeto de base de datos proporciona una interfaz al origen de datos.|
|Enlazar columnas de datos al conjunto de registros dinámicamente.|En ODBC, agregue código a la clase de conjunto de registros derivada para administrar el enlace. Consulte el artículo [Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||

## <a name="see-also"></a>Consulte también

[Compilar en el marco](../mfc/building-on-the-framework.md)<br/>
[Secuencia de operaciones para compilar aplicaciones MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Secuencia de operaciones para crear aplicaciones OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Secuencia de operaciones para crear controles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
