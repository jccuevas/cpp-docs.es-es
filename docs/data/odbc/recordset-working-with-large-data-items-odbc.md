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
ms.openlocfilehash: b84365461ce6d45fccdf1922974feff5af93f99f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212763"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Conjunto de registros: Trabajar con grandes elementos de datos (ODBC)

Este tema se aplica a las clases ODBC de MFC y a las clases DAO de MFC.

> [!NOTE]
>  Si utiliza las clases DAO de MFC, administre los elementos de datos de gran tamaño con la clase [CByteArray](../../mfc/reference/cbytearray-class.md) en lugar de la clase [CLongBinary](../../mfc/reference/clongbinary-class.md). Si utiliza las clases ODBC de MFC con la obtención masiva de filas, use `CLongBinary` en lugar de `CByteArray`. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Supongamos que la base de datos puede almacenar grandes fragmentos de datos, como mapas de bits (fotografías de empleados, mapas, imágenes de productos, objetos OLE, etc.). Este tipo de datos a menudo se conoce como un objeto binario grande (o BLOB) porque:

- Cada valor de campo es grande.

- A diferencia de los números y otros tipos de datos simples, no tiene ningún tamaño predecible.

- Los datos no son correctos desde la perspectiva del programa.

En este tema se explica qué es compatible con las clases de base de datos para trabajar con estos objetos.

##  <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>Administrar objetos grandes

Los conjuntos de registros tienen dos maneras de resolver la dificultad especial de administración de objetos binarios grandes. Puede usar la clase [CByteArray](../../mfc/reference/cbytearray-class.md) o puede usar la clase [CLongBinary](../../mfc/reference/clongbinary-class.md). En general, `CByteArray` es la manera preferida de administrar datos binarios de gran tamaño.

`CByteArray` requiere más sobrecarga que `CLongBinary` pero es más capaz, como se describe en [la clase CByteArray](#_core_the_cbytearray_class). `CLongBinary` se describe brevemente en [la clase CLongBinary](#_core_the_clongbinary_class).

Para obtener información detallada sobre el uso de `CByteArray` para trabajar con elementos de datos de gran tamaño, vea la [Nota técnica 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>CByteArray (clase)

`CByteArray` es una de las clases de colección de MFC. Un objeto `CByteArray` almacena una matriz dinámica de bytes; la matriz puede crecer si es necesario. La clase proporciona un acceso rápido por índice, al igual que con C++ las matrices integradas. `CByteArray` objetos se pueden serializar y volcar con fines de diagnóstico. La clase proporciona funciones miembro para obtener y establecer los bytes especificados, insertar y anexar bytes, y quitar un byte o todos los bytes. Estas funciones facilitan el análisis de los datos binarios. Por ejemplo, si el objeto binario es un objeto OLE, puede que tenga que trabajar con algunos bytes de encabezado para alcanzar el objeto real.

##  <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>Usar CByteArray en conjuntos de registros

Al conceder a un miembro de datos de campo del conjunto de registros el tipo `CByteArray`, se proporciona una base fija a partir de la cual [RFX](../../data/odbc/record-field-exchange-rfx.md) puede administrar la transferencia de dicho objeto entre el conjunto de registros y el origen de datos, y a través del cual se pueden manipular los datos dentro del objeto. RFX necesita un sitio específico para los datos recuperados y necesita una manera de tener acceso a los datos subyacentes.

Para obtener información detallada sobre el uso de `CByteArray` para trabajar con elementos de datos de gran tamaño, vea la [Nota técnica 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>CLongBinary (clase)

Un objeto [CLongBinary](../../mfc/reference/clongbinary-class.md) es un shell sencillo en torno a un identificador `HGLOBAL` a un bloque de almacenamiento asignado en el montón. Cuando enlaza una columna de tabla que contiene un objeto binario grande, RFX asigna el identificador de `HGLOBAL` cuando necesita transferir los datos al conjunto de registros y almacena el identificador en el campo `CLongBinary` del conjunto de registros.

A su vez, utilice el controlador de `HGLOBAL`, `m_hData`, para trabajar con los datos en sí, como lo haría con cualquier dato de controlador. Aquí es donde [CByteArray](../../mfc/reference/cbytearray-class.md) agrega funcionalidades.

> [!CAUTION]
>  Los objetos CLongBinary no se pueden usar como parámetros en las llamadas de función. Además, su implementación, que llama a `::SQLGetData`, necesariamente ralentiza el rendimiento del desplazamiento para una instantánea desplazable. Esto también puede suceder cuando se usa una `::SQLGetData` llamar a sí mismo para recuperar columnas de esquema dinámico.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)
