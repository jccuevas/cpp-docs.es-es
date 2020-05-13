---
title: 'Conjunto de registros: Trabajar con grandes elementos de datos (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 872fa7229738314b86b6ae6c0d5dc5a5562b27f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360602"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Conjunto de registros: Trabajar con grandes elementos de datos (ODBC)

Este tema se aplica tanto a las clases ODBC de MFC como a las clases DAO de MFC.

> [!NOTE]
> Si utiliza las clases DAO de MFC, administre los elementos de datos grandes con la clase [CByteArray](../../mfc/reference/cbytearray-class.md) en lugar de la clase [CLongBinary](../../mfc/reference/clongbinary-class.md). Si utiliza las clases ODBC de MFC `CLongBinary` con `CByteArray`la obtención masiva de filas, use en lugar de . Para obtener más información acerca de la obtención masiva de filas, vea [Conjunto de registros: obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Supongamos que la base de datos puede almacenar grandes fragmentos de datos, como mapas de bits (fotografías de empleados, mapas, imágenes de productos, objetos OLE, etc.). Este tipo de datos se conoce a menudo como un objeto binario grande (o BLOB) porque:

- Cada valor de campo es grande.

- A diferencia de los números y otros tipos de datos simples, no tiene un tamaño predecible.

- Los datos no tienen forma desde la perspectiva de su programa.

En este tema se explica qué compatibilidad proporcionan las clases de base de datos para trabajar con estos objetos.

## <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>Gestión de objetos grandes

Los conjuntos de registros tienen dos maneras de resolver la dificultad especial de administrar objetos binarios grandes. Puede utilizar la clase [CByteArray](../../mfc/reference/cbytearray-class.md) o la clase [CLongBinary](../../mfc/reference/clongbinary-class.md). En general, `CByteArray` es la forma preferida de administrar datos binarios grandes.

`CByteArray`requiere más sobrecarga `CLongBinary` que, pero es más capaz, como se describe en [la clase CByteArray](#_core_the_cbytearray_class). `CLongBinary`se describe brevemente en [The CLongBinary Class](#_core_the_clongbinary_class).

Para obtener información `CByteArray` detallada sobre el uso para trabajar con elementos de datos grandes, consulte [nota técnica 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>Clase CByteArray

`CByteArray`es una de las clases de colección MFC. Un `CByteArray` objeto almacena una matriz dinámica de bytes: la matriz puede crecer si es necesario. La clase proporciona un acceso rápido por índice, al igual que con las matrices C++ integradas. `CByteArray`objetos se pueden serializar y volcar con fines de diagnóstico. La clase proporciona funciones miembro para obtener y establecer bytes especificados, insertar y anexar bytes y quitar un byte o todos los bytes. Estas instalaciones facilitan el análisis de los datos binarios. Por ejemplo, si el objeto binario es un objeto OLE, es posible que tenga que trabajar a través de algunos bytes de encabezado para llegar al objeto real.

## <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>Uso de CByteArray en conjuntos de registros

Al proporcionar a un miembro de `CByteArray`datos de campo del conjunto de registros el tipo , se proporciona una base fija desde la que [RFX](../../data/odbc/record-field-exchange-rfx.md) puede administrar la transferencia de un objeto de este tipo entre el conjunto de registros y el origen de datos y a través del cual se pueden manipular los datos dentro del objeto. RFX necesita un sitio específico para los datos recuperados y necesita una forma de tener acceso a los datos subyacentes.

Para obtener información `CByteArray` detallada sobre el uso para trabajar con elementos de datos grandes, consulte [nota técnica 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>Clase CLongBinary

Un [CLongBinary](../../mfc/reference/clongbinary-class.md) objeto es un `HGLOBAL` shell simple alrededor de un identificador a un bloque de almacenamiento asignado en el montón. Cuando enlaza una columna de tabla que contiene un `HGLOBAL` objeto binario grande, RFX asigna el identificador cuando `CLongBinary` necesita transferir los datos al conjunto de registros y almacena el identificador en el campo del conjunto de registros.

A su vez, `HGLOBAL` se `m_hData`utiliza el identificador, , para trabajar con los datos en sí, operando en él como lo haría en cualquier dato de identificador. Aquí es donde [CByteArray](../../mfc/reference/cbytearray-class.md) agrega capacidades.

> [!CAUTION]
> CLongBinary objetos no se pueden utilizar como parámetros en las llamadas de función. Además, su implementación, que llama `::SQLGetData`a , ralentiza necesariamente el rendimiento de desplazamiento para una instantánea desplazable. Esto también puede ser cierto `::SQLGetData` cuando se usa una llamada usted mismo para recuperar columnas de esquema dinámico.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)
