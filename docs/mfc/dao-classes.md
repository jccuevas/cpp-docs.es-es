---
title: Clases de DAO
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 51abd29ef4de5d70f4a5b2b6b14b53510e7876a1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615933"
---
# <a name="dao-classes"></a>Clases de DAO

DAO se utiliza con bases de datos de Access y se admite a través de Office 2013. DAO 3,6 es la versión final y se considera obsoleta.

Estas clases funcionan con las demás clases de marco de trabajo de la aplicación para proporcionar un acceso sencillo a las bases de datos del objeto de acceso a datos (DAO), que usan el mismo motor de base de datos que Microsoft Visual Basic y Microsoft Access. Las clases DAO también pueden tener acceso a una gran variedad de bases de datos para las que están disponibles controladores ODBC (Conectividad abierta de bases de datos).

Los programas que utilizan bases de datos DAO tendrán al menos un `CDaoDatabase` objeto y un `CDaoRecordset` objeto.

> [!NOTE]
> El entorno de Visual C++ y los asistentes ya no admiten DAO (aunque las clases DAO están incluidas y todavía se pueden usar). Microsoft recomienda usar ODBC para los nuevos proyectos de MFC. Solo se debe utilizar DAO en el mantenimiento de las aplicaciones existentes.

[CDaoWorkspace](reference/cdaoworkspace-class.md)<br/>
Administra una sesión de base de datos con nombre y protegida mediante contraseña de inicio de sesión a cierre de sesión. La mayoría de los programas usan el área de trabajo predeterminada.

[CDaoDatabase](reference/cdaodatabase-class.md)<br/>
Conexión a una base de datos a través de la cual se puede trabajar con los datos.

[CDaoRecordset](reference/cdaorecordset-class.md)<br/>
Representa un conjunto de registros seleccionados de un origen de datos.

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
Una vista que muestra registros de una base de datos en controles.

[CDaoQueryDef](reference/cdaoquerydef-class.md)<br/>
Representa una definición de consulta, normalmente una guardada en una base de datos.

[CDaoTableDef](reference/cdaotabledef-class.md)<br/>
Representa la definición almacenada de una tabla base o una tabla asociada.

[CDaoException](reference/cdaoexception-class.md)<br/>
Representa una condición de excepción que surge de las clases DAO.

[CDaoFieldExchange](reference/cdaofieldexchange-class.md)<br/>
Admite las rutinas de intercambio de campos del registro (DFX) de DAO utilizadas por las clases de base de datos DAO. Normalmente no se utilizará esta clase directamente.

## <a name="related-classes"></a>Clases relacionadas

[CLongBinary](reference/clongbinary-class.md)<br/>
Encapsula un identificador para el almacenamiento de un objeto binario grande (BLOB), como un mapa de bits. `CLongBinary`los objetos se utilizan para administrar objetos de datos de gran tamaño almacenados en tablas de base de datos.

[COleCurrency](reference/colecurrency-class.md)<br/>
Contenedor de la **moneda**del tipo de automatización OLE, un tipo aritmético de punto fijo, con 15 dígitos delante del separador decimal y 4 dígitos después de.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Contenedor para la **fecha**de tipo de automatización OLE. Representa valores de fecha y hora.

[COleVariant](reference/colevariant-class.md)<br/>
Contenedor de la **variante**de tipo de automatización OLE. Los datos de la **variante**s se pueden almacenar en muchos formatos.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
