---
title: Clases de ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
ms.openlocfilehash: 18b6e3a0ea20dbd352a61c4faab52c35b852dcb3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622190"
---
# <a name="odbc-classes"></a>Clases de ODBC

Estas clases funcionan con las demás clases de marco de trabajo de la aplicación para proporcionar un acceso sencillo a una amplia variedad de bases de datos para las que están disponibles controladores ODBC (Conectividad abierta de bases de datos).

Los programas que utilizan bases de datos ODBC tendrán al menos un `CDatabase` objeto y un `CRecordset` objeto.

[CDatabase](reference/cdatabase-class.md)<br/>
Encapsula una conexión a un origen de datos, a través de la cual puede trabajar en el origen de datos.

[CRecordset](reference/crecordset-class.md)<br/>
Encapsula un conjunto de registros seleccionados de un origen de datos. Los conjuntos de registros permiten desplazarse de registro a registro, actualizar registros (agregar, editar y eliminar registros), calificar la selección con un filtro, ordenar la selección y parametrizar la selección con información obtenida o calculada en tiempo de ejecución.

[CRecordView](reference/crecordview-class.md)<br/>
Proporciona una vista de formulario conectada directamente a un objeto de conjunto de registros. El mecanismo de intercambio de datos de cuadros de diálogo (DDX) intercambia datos entre el conjunto de registros y los controles de la vista de registros. Al igual que todas las vistas de formulario, una vista de registros se basa en un recurso de plantilla de cuadro de diálogo. Las vistas de registros también permiten pasar de un registro a un registro en el conjunto de registros, actualizar registros y cerrar el conjunto de registros asociado cuando se cierra la vista de registros.

[CDBException](reference/cdbexception-class.md)<br/>
Excepción que resulta de errores en el procesamiento del acceso a datos. Esta clase tiene la misma finalidad que otras clases de excepción en el mecanismo de control de excepciones de la biblioteca de clases.

[CFieldExchange](reference/cfieldexchange-class.md)<br/>
Proporciona información de contexto para admitir el intercambio de campos de registros (RFX), que intercambia datos entre los miembros de datos de campo y los miembros de datos de parámetro de un objeto de conjunto de registros y las columnas de tabla correspondientes en el origen de datos. Análogo a la clase [CDataExchange (](reference/cdataexchange-class.md), que se utiliza de forma similar para el intercambio de datos de cuadros de diálogo (DDX).

## <a name="related-classes"></a>Clases relacionadas

[CLongBinary](reference/clongbinary-class.md)<br/>
Encapsula un identificador para el almacenamiento de un objeto binario grande (BLOB), como un mapa de bits. `CLongBinary`los objetos se utilizan para administrar objetos de datos de gran tamaño almacenados en tablas de base de datos.

[CDBVariant](reference/cdbvariant-class.md)<br/>
Permite almacenar un valor sin preocuparse por el tipo de datos del valor. `CDBVariant`realiza un seguimiento del tipo de datos del valor actual, que se almacena en una Unión.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
