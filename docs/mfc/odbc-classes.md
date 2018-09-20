---
title: Clases ODBC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97bbdb74d122e633574dcf76876f0907de8ef2c4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400589"
---
# <a name="odbc-classes"></a>Clases de ODBC

Estas clases funcionan con las otras clases de marco de aplicación para proporcionar acceso fácil a una amplia variedad de bases de datos para el que están disponibles los controladores de Open Database Connectivity (ODBC).

Programas que utilizan las bases de datos ODBC tendrá al menos un `CDatabase` objeto y un `CRecordset` objeto.

[CDatabase](../mfc/reference/cdatabase-class.md)<br/>
Encapsula una conexión a un origen de datos a través del cual se puede operar en el origen de datos.

[CRecordset](../mfc/reference/crecordset-class.md)<br/>
Encapsula un conjunto de registros seleccionados de un origen de datos. Conjuntos de registros permiten desplazarse por los registros, actualizando los registros (adición, edición y eliminación de registros), la selección de calificación con un filtro, la selección de ordenación y parametrizar la selección con información obtenida o calculada en tiempo de ejecución.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Proporciona un formulario de vista directamente conectada a un objeto de conjunto de registros. Los datos de cuadro de diálogo (DDX) mecanismo intercambia datos entre el conjunto de registros y los controles de la vista de registros de exchange. Al igual que todas las vistas de formulario, una vista de registros se basa en un recurso de plantilla de cuadro de diálogo. Vistas de registros también admiten mover por los registros del conjunto de registros, actualizar los registros y cierra el conjunto de registros asociado cuando se cierra la vista de registros.

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
Una excepción resultante de errores de acceso a datos de procesamiento. Esta clase tiene la misma finalidad que otras clases de excepción en el mecanismo de control de excepciones de la biblioteca de clases.

[CFieldExchange](../mfc/reference/cfieldexchange-class.md)<br/>
Proporciona información de contexto para admitir el intercambio de campos de registros (RFX), que intercambia datos entre los miembros de datos de campo y los miembros de datos de parámetro de un objeto de conjunto de registros y las columnas de tabla correspondiente en el origen de datos. Análoga a la clase [CDataExchange](../mfc/reference/cdataexchange-class.md), que se usa de forma similar para el intercambio de datos de cuadro de diálogo (DDX).

## <a name="related-classes"></a>Clases relacionadas

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Encapsula un identificador para el almacenamiento para un objeto binario grande (BLOB), como un mapa de bits. `CLongBinary` los objetos se usan para administrar los objetos de gran cantidad de datos almacenados en tablas de base de datos.

[CDBVariant](../mfc/reference/cdbvariant-class.md)<br/>
le permite almacenar un valor sin preocuparse sobre el tipo de datos del valor. `CDBVariant` realiza un seguimiento del tipo de datos del valor actual, que se almacena en una unión.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

