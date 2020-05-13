---
title: Clases de DAO
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 7ae85cbeb7790cadb8c26dfbdb7a5163dbcd47c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373515"
---
# <a name="dao-classes"></a>Clases de DAO

DAO se usa con bases de datos de Access y se admite a través de Office 2013. DAO 3.6 es la versión final, y se considera obsoleto.

Estas clases funcionan con las otras clases de marco de trabajo de aplicación para facilitar el acceso a las bases de datos de objetos de acceso a datos (DAO), que usan el mismo motor de base de datos que Microsoft Visual Basic y Microsoft Access. Las clases DAO también pueden tener acceso a una amplia variedad de bases de datos para las que están disponibles controladores de conectividad abierta de base de datos (ODBC).

Los programas que utilizan bases `CDaoDatabase` de datos `CDaoRecordset` DAO tendrán al menos un objeto y un objeto.

> [!NOTE]
> El entorno y los asistentes de Visual C++ ya no admiten DAO (aunque las clases DAO están incluidas y todavía puede usarlas). Microsoft recomienda usar ODBC para nuevos proyectos MFC. Solo debe usar DAO para mantener las aplicaciones existentes.

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Administra una sesión de base de datos con nombre protegida por contraseña desde el inicio de sesión hasta el cierre de sesión. La mayoría de los programas utilizan el espacio de trabajo predeterminado.

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Una conexión a una base de datos a través de la cual puede operar en los datos.

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Representa un conjunto de registros seleccionados de un origen de datos.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Una vista que muestra registros de una base de datos en controles.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Representa una definición de consulta, normalmente una guardada en una base de datos.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Representa la definición almacenada de una tabla base o una tabla asociada.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Representa una condición de excepción derivada de las clases DAO.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Admite las rutinas de intercambio de campos del registro (DFX) de DAO utilizadas por las clases de base de datos DAO. Normalmente no usará directamente esta clase.

## <a name="related-classes"></a>Clases relacionadas

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Encapsula un identificador de almacenamiento para un objeto binario grande (BLOB), como un mapa de bits. `CLongBinary`los objetos se utilizan para administrar objetos de datos grandes almacenados en tablas de base de datos.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Wrapper para el tipo de automatización OLE **CURRENCY**, un tipo aritmético de punto fijo, con 15 dígitos antes del punto decimal y 4 dígitos después.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Contenedor para el tipo de automatización OLE **DATE**. Representa los valores de fecha y hora.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Contenedor para el tipo de automatización OLE **VARIANT**. Los datos de **VARIANT**s se pueden almacenar en muchos formatos.

## <a name="see-also"></a>Consulte también

[Información general de clases](../mfc/class-library-overview.md)
