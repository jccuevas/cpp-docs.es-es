---
title: 'Conjunto de registros: Trabajar con grandes elementos de datos (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6845d2e3c1b1eac31486200a0f610037d4774626
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Conjunto de registros: Trabajar con grandes elementos de datos (ODBC)
En este tema se aplica a las clases ODBC de MFC y las clases DAO de MFC.  
  
> [!NOTE]
>  Si está utilizando las clases DAO de MFC, administrar los elementos de datos de gran tamaño mediante la clase [CByteArray](../../mfc/reference/cbytearray-class.md) en lugar de la clase [CLongBinary](../../mfc/reference/clongbinary-class.md). Si se están utilizando las clases ODBC de MFC con la obtención masiva de filas, use `CLongBinary` en lugar de `CByteArray`. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Suponga que la base de datos puede almacenar grandes fragmentos de datos, como mapas de bits (fotografías de los empleados, mapas, imágenes de productos, objetos OLE y así sucesivamente). Este tipo de datos a menudo se conoce como un objeto binario grande (BLOB) porque:  
  
-   Cada valor del campo es grande.  
  
-   A diferencia de los números y otros tipos de datos simples, no tiene ningún tamaño de predicción.  
  
-   Los datos son no tienen formless desde la perspectiva del programa.  
  
 Este tema explica la compatibilidad que proporcionan las clases de base de datos para trabajar con estos objetos.  
  
##  <a name="_core_managing_large_objects"></a> Administrar objetos grandes  
 Conjuntos de registros tienen dos formas de resolver la especial dificultad de administrar objetos binarios grandes. Puede utilizar la clase [CByteArray](../../mfc/reference/cbytearray-class.md) o puede utilizar la clase [CLongBinary](../../mfc/reference/clongbinary-class.md). En general, `CByteArray` es la mejor manera de administrar datos binarios de gran tamaño.  
  
 `CByteArray` requiere más sobrecarga que `CLongBinary` pero tiene mayor capacidad, como se describe en [la clase CByteArray](#_core_the_cbytearray_class). `CLongBinary` se describe brevemente en [CLongBinary (clase)](#_core_the_clongbinary_class).  
  
 Para obtener información detallada sobre el uso de `CByteArray` para trabajar con grandes elementos de datos, vea [Nota técnica 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).  
  
##  <a name="_core_the_cbytearray_class"></a> CByteArray (clase)  
 `CByteArray` es una de las clases de colección de MFC. Un `CByteArray` objeto almacena una matriz dinámica de bytes, la matriz puede crecer según sea necesario. La clase proporciona un acceso rápido por índice, al igual que con las matrices de C++ integradas. `CByteArray` pueden serializar objetos y volcarse con fines de diagnóstico. La clase proporciona funciones miembro para obtener y establecer bytes específicos, insertar y anexar bytes y quitar un byte o todos los bytes. Estas funciones simplifican el análisis de los datos binarios más fáciles. Por ejemplo, si el objeto binario es un objeto OLE, podría tener que trabajar a través de algunos bytes de encabezado para llegar al objeto real.  
  
##  <a name="_core_using_cbytearray_in_recordsets"></a> Utilizar CByteArray en conjuntos de registros  
 Proporcionando el tipo de un miembro de datos de campo del conjunto de registros `CByteArray`, se proporciona una base fija desde el que [RFX](../../data/odbc/record-field-exchange-rfx.md) puede administrar la transferencia de este tipo de objeto entre el conjunto de registros y el origen de datos y a través de que se puede manipular el datos que contiene el objeto. RFX necesita una ubicación específica para los datos recuperados y necesita una manera de tener acceso a los datos subyacentes.  
  
 Para obtener información detallada sobre el uso de `CByteArray` para trabajar con grandes elementos de datos, vea [Nota técnica 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).  
  
##  <a name="_core_the_clongbinary_class"></a> CLongBinary (clase)  
 A [CLongBinary](../../mfc/reference/clongbinary-class.md) objeto es un shell sencillo alrededor de una `HGLOBAL` controlar en un bloque de almacenamiento asignado en el montón. Cuando enlaza una columna de tabla que contiene un objeto binario grande, RFX asigna el `HGLOBAL` controlar cuando se necesita transferir los datos al conjunto de registros y almacena el identificador en el `CLongBinary` campo del conjunto de registros.  
  
 A su vez, use la `HGLOBAL` controlar, `m_hData`, para trabajar con los datos en Sí, funciona en él, igual que haría en cualquier datos. Aquí es donde [CByteArray](../../mfc/reference/cbytearray-class.md) agrega capacidades.  
  
> [!CAUTION]
>  Los objetos CLongBinary no se puede usar como parámetros en llamadas a funciones. Asimismo, su implementación, que llama **:: SQLGetData**, necesariamente ralentiza el rendimiento de desplazamiento para una instantánea desplazable. Esto también puede suceder cuando se usa un **:: SQLGetData** llamar a sí mismo para recuperar columnas de esquema dinámicas.  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)