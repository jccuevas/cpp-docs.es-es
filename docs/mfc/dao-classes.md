---
title: Clases de DAO
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 238aab0a1948f16a85b8ea16719b75b49f5e69c8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287497"
---
# <a name="dao-classes"></a>Clases de DAO

Estas clases funcionan con las otras clases de marco de aplicación para proporcionar acceso fácil a las bases de datos de objeto de acceso a datos (DAO), que usan el mismo motor de base de datos como Microsoft Visual Basic y Microsoft Access. Las clases DAO también pueden tener acceso a una amplia variedad de bases de datos para el que están disponibles los controladores de Open Database Connectivity (ODBC).

Programas que utilizan las bases de datos DAO tendrá al menos un `CDaoDatabase` objeto y un `CDaoRecordset` objeto.

> [!NOTE]
>  Los asistentes y el entorno de Visual C++ ya no admiten DAO (aunque las clases DAO están incluidas y puede seguir usándolos). Microsoft recomienda que utilice ODBC para nuevos proyectos de MFC. Sólo se debe utilizar DAO mantener las aplicaciones existentes.

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Administra una sesión de base de datos con nombre, protegida por contraseña de inicio de sesión para cerrar la sesión. Mayoría de los programas utilice el área de trabajo predeterminada.

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Una conexión a una base de datos a través del cual se puede operar en los datos.

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Representa un conjunto de registros seleccionados de un origen de datos.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Una vista que muestra registros de una base de datos en controles.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Representa una definición de consulta, normalmente uno guardado en una base de datos.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Representa la definición almacenada de una tabla base o una tabla asociada.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Representa una condición de excepción que surge de las clases DAO.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Admite las rutinas de intercambio de campos del registro (DFX) de DAO utilizadas por las clases de base de datos DAO. Normalmente no usará directamente esta clase.

## <a name="related-classes"></a>Clases relacionadas

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Encapsula un identificador para el almacenamiento para un objeto binario grande (BLOB), como un mapa de bits. `CLongBinary` los objetos se usan para administrar los objetos de gran cantidad de datos almacenados en tablas de base de datos.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Contenedor para el tipo de automatización OLE **moneda**, un tipo aritmético de punto fijo, con 15 dígitos anteriores al separador decimal y 4 dígitos después.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Contenedor para el tipo de automatización OLE **fecha**. Representa valores de fecha y hora.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Contenedor para el tipo de automatización OLE **VARIANT**. Datos de **VARIANT**s pueden almacenarse en muchos formatos.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
