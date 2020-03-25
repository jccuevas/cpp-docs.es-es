---
title: 'Conjunto de registros: Desplazamiento (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets [C++], end of
- recordsets [C++], beginning of
- navigation [C++], recordsets
- recordsets [C++], moving to records
- ODBC recordsets, scrolling
- recordsets [C++], navigating
- scrolling [C++], recordsets
- Move method (recordsets)
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
ms.openlocfilehash: 8a8305d2acacc79f5d7fe395087a0bd13dcbd196
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212776"
---
# <a name="recordset-scrolling-odbc"></a>Conjunto de registros: Desplazamiento (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Después de abrir un conjunto de registros, debe tener acceso a los registros para mostrar valores, realizar cálculos, generar informes, etc. El desplazamiento permite desplazarse de un registro a otro dentro del conjunto de registros.

En este tema se explica:

- [Cómo desplazarse de un registro a otro en un conjunto de registros](#_core_scrolling_from_one_record_to_another).

- [En qué circunstancias es el desplazamiento y no se admite](#_core_when_scrolling_is_supported).

##  <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>Desplazarse de un registro a otro

La clase `CRecordset` proporciona las funciones miembro de `Move` para el desplazamiento dentro de un conjunto de registros. Estas funciones mueven el registro actual por conjuntos de filas. Si ha implementado la obtención masiva de filas, una operación `Move` recoloca el conjunto de registros por el tamaño del conjunto de filas. Si no ha implementado la obtención masiva de filas, una llamada a una función `Move` recoloca el conjunto de registros en un registro cada vez. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Al desplazarse por un conjunto de registros, es posible que los registros eliminados no se omitan. Para obtener más información, vea la función miembro [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) .

Además de las funciones de `Move`, `CRecordset` proporciona funciones miembro para comprobar si se ha desplazado más allá del final del conjunto de registros.

Para determinar si el desplazamiento es posible en el conjunto de registros, llame a la función miembro `CanScroll`.

#### <a name="to-scroll"></a>Para desplazarse

1. Reenviar un registro o un conjunto de filas: llame a la función miembro [MoveNext](../../mfc/reference/crecordset-class.md#movenext) .

1. Retroceder un registro o un conjunto de filas: llama a la función miembro [MovePrev](../../mfc/reference/crecordset-class.md#moveprev) .

1. Al primer registro del conjunto de registros: llame a la función miembro [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) .

1. En el último registro del conjunto de registros o en el último conjunto de filas: llame a la función miembro [MoveLast](../../mfc/reference/crecordset-class.md#movelast) .

1. *N* registros en relación con la posición actual: llame a la función miembro [Move](../../mfc/reference/crecordset-class.md#move) .

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Para probar el final o el principio del conjunto de registros

1. ¿Ha desplazado más allá del último registro? Llame a la función miembro [IsEOF](../../mfc/reference/crecordset-class.md#iseof) .

1. ¿Se ha desplazado hacia atrás en el primer registro (en movimiento hacia atrás)? Llame a la función miembro [IsBOF](../../mfc/reference/crecordset-class.md#isbof) .

En el ejemplo de código siguiente se usa `IsBOF` y `IsEOF` para detectar los límites de un conjunto de registros al desplazarse en cualquier dirección.

```
// Open a recordset; first record is current
CCustSet rsCustSet( NULL );
rsCustSet.Open( );

if( rsCustSet.IsBOF( ) )
    return;
    // The recordset is empty

// Scroll to the end of the recordset, past
// the last record, so no record is current
while ( !rsCustSet.IsEOF( ) )
    rsCustSet.MoveNext( );

// Move to the last record
rsCustSet.MoveLast( );

// Scroll to beginning of the recordset, before
// the first record, so no record is current
while( !rsCustSet.IsBOF( ) )
    rsCustSet.MovePrev( );

// First record is current again
rsCustSet.MoveFirst( );
```

`IsEOF` devuelve un valor distinto de cero si el conjunto de registros se coloca después del último registro. `IsBOF` devuelve un valor distinto de cero si el conjunto de registros se coloca delante del primer registro (antes de todos los registros). En cualquier caso, no hay ningún registro actual en el que operar. Si llama a `MovePrev` cuando `IsBOF` ya es TRUE o llama a `MoveNext` cuando `IsEOF` ya es TRUE, el marco de trabajo produce una `CDBException`. También puede usar `IsBOF` y `IsEOF` para comprobar si hay un conjunto de registros vacío.

Para obtener más información sobre la navegación por conjuntos de registros, vea [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>Cuando se admite el desplazamiento

Como se diseñó originalmente, SQL solo proporcionó el desplazamiento hacia delante, pero ODBC extiende las capacidades de desplazamiento. El nivel de compatibilidad disponible para el desplazamiento depende de los controladores ODBC con los que funciona la aplicación, el nivel de cumplimiento de la API de ODBC del controlador y de si la biblioteca de cursores ODBC se carga en la memoria. Para obtener más información, vea [ODBC](../../data/odbc/odbc-basics.md) y [ODBC: biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
>  Puede controlar si se utiliza la biblioteca de cursores. Vea los parámetros *bUseCursorLib* y *dwOptions* en [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
>  A diferencia de las clases DAO de MFC, las clases ODBC de MFC no proporcionan un conjunto de funciones `Find` para buscar el Registro siguiente (o anterior) que cumple los criterios especificados.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:: CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset:: CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Conjunto de registros: Filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
