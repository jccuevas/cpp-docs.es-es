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
ms.openlocfilehash: 3ba8d4af5b0781c425dd3b1223e2208b279f055e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033049"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Conjunto de registros: Trabajar con grandes elementos de datos (ODBC)

En este tema se aplica a las clases ODBC de MFC y las clases DAO de MFC.

> [!NOTE]
>  Si utiliza las clases DAO de MFC, administrar los elementos de datos de gran tamaño con la clase [CByteArray](../../mfc/reference/cbytearray-class.md) en lugar de la clase [CLongBinary](../../mfc/reference/clongbinary-class.md). Si utiliza las clases ODBC de MFC con la obtención masiva de filas, use `CLongBinary` lugar `CByteArray`. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: Obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Supongamos que la base de datos puede almacenar grandes conjuntos de datos, como mapas de bits (fotografías de los empleados, mapas, imágenes de productos, los objetos OLE y así sucesivamente). Este tipo de datos a menudo se conoce como un objeto binario grande (o BLOB) porque:

- Cada valor del campo es grande.

- A diferencia de los números y otros tipos de datos simples, no tiene ningún tamaño predecible.

- Los datos son no tienen formless desde la perspectiva del programa.

En este tema se explica la compatibilidad que proporcionan las clases de base de datos para trabajar con estos objetos.

##  <a name="_core_managing_large_objects"></a> Administrar objetos grandes

Conjuntos de registros tienen dos formas de solucionar las dificultades especiales de la administración de objetos binarios grandes. Puede usar la clase [CByteArray](../../mfc/reference/cbytearray-class.md) o puede usar la clase [CLongBinary](../../mfc/reference/clongbinary-class.md). En general, `CByteArray` es la mejor manera de administrar datos binarios grandes.

`CByteArray` requiere más sobrecarga que `CLongBinary` pero tiene mayor capacidad, como se describe en [CByteArray (clase)](#_core_the_cbytearray_class). `CLongBinary` se describe brevemente en [CLongBinary (clase)](#_core_the_clongbinary_class).

Para obtener información detallada sobre el uso de `CByteArray` para trabajar con grandes elementos de datos, consulte [Nota técnica 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="_core_the_cbytearray_class"></a> CByteArray (clase)

`CByteArray` es una de las clases de colección de MFC. Un `CByteArray` objeto almacena una matriz dinámica de bytes, la matriz puede crecer según sea necesario. La clase proporciona un acceso rápido por índice, al igual que con las matrices de C++ integradas. `CByteArray` se pueden serializar objetos y volcarse para fines de diagnóstico. La clase proporciona funciones miembro para obtener y establecer los bytes especificados, insertar y anexar bytes y quitar un byte o todos los bytes. Estas funciones simplifican el análisis de los datos binarios. Por ejemplo, si el objeto binario es un objeto OLE, tendrá que trabajar a través de algunos bytes de encabezado para alcanzar el objeto real.

##  <a name="_core_using_cbytearray_in_recordsets"></a> Uso de CByteArray en conjuntos de registros

Proporcionando el tipo de un miembro de datos de campo del conjunto de registros `CByteArray`, proporciona una base fija desde el que [RFX](../../data/odbc/record-field-exchange-rfx.md) puede administrar la transferencia de este tipo de objeto entre el conjunto de registros y el origen de datos y a través de lo que puede manipular el datos dentro del objeto. RFX necesita un sitio específico para los datos recuperados y necesita una manera de tener acceso a los datos subyacentes.

Para obtener información detallada sobre el uso de `CByteArray` para trabajar con grandes elementos de datos, consulte [Nota técnica 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="_core_the_clongbinary_class"></a> CLongBinary (clase)

Un [CLongBinary](../../mfc/reference/clongbinary-class.md) objeto es un shell sencillo en torno a un `HGLOBAL` identificador de un bloque de almacenamiento asignado en el montón. Cuando se enlaza una columna de tabla que contiene un objeto binario grande, RFX asigna el `HGLOBAL` controlar cuando necesita transferir los datos al conjunto de registros y almacena el identificador en el `CLongBinary` campo del conjunto de registros.

A su vez, usa el `HGLOBAL` controlar, `m_hData`, para trabajar con los datos, operar en ella se harían en cualquier datos de controlar. Aquí es donde [CByteArray](../../mfc/reference/cbytearray-class.md) agrega capacidades.

> [!CAUTION]
>  Los objetos CLongBinary no se puede usar como parámetros en las llamadas de función. Además, su implementación, que llama `::SQLGetData`, necesariamente ralentiza el rendimiento de desplazamiento para una instantánea desplazable. Esto también puede suceder cuando se usa un `::SQLGetData` llamar a sí mismo para recuperar las columnas de esquema dinámico.

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)