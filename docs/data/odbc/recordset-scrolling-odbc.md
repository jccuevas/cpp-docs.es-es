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
ms.openlocfilehash: 931051296dff495939fcbd894102a1b00e48ee90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366937"
---
# <a name="recordset-scrolling-odbc"></a>Conjunto de registros: Desplazamiento (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Después de abrir un conjunto de registros, debe tener acceso a los registros para mostrar valores, realizar cálculos, generar informes, etc. El desplazamiento le permite pasar de un registro a otro dentro del conjunto de registros.

En este tema se explica:

- [Cómo desplazarse de un registro a otro en un conjunto de registros.](#_core_scrolling_from_one_record_to_another)

- [¿En qué circunstancias se admite y no se admite el desplazamiento.](#_core_when_scrolling_is_supported)

## <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>Desplazamiento de un registro a otro

Clase `CRecordset` proporciona `Move` las funciones miembro para desplazarse dentro de un conjunto de registros. Estas funciones mueven el registro actual por conjuntos de filas. Si ha implementado la obtención `Move` masiva de filas, una operación cambia la posición del conjunto de registros por el tamaño del conjunto de filas. Si no ha implementado la obtención masiva `Move` de filas, una llamada a una función cambia la posición del conjunto de registros por un registro cada vez. Para obtener más información acerca de la obtención masiva de filas, vea [Conjunto de registros: obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
> Al desplazarse por un conjunto de registros, es posible que no se omitan los registros eliminados. Para obtener más información, vea el [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) función miembro.

Además `Move` de `CRecordset` las funciones, proporciona funciones miembro para comprobar si se ha desplazado más allá del final o por delante del principio del conjunto de registros.

Para determinar si el desplazamiento es posible `CanScroll` en el conjunto de registros, llame a la función miembro.

#### <a name="to-scroll"></a>Para desplazarse

1. Reenviar un registro o un conjunto de filas: llame a la [MoveNext](../../mfc/reference/crecordset-class.md#movenext) función miembro.

1. Retroceder un registro o un conjunto de filas: llame a la [MovePrev](../../mfc/reference/crecordset-class.md#moveprev) función miembro.

1. Para el primer registro del conjunto de registros: llame a la función miembro [MoveFirst.](../../mfc/reference/crecordset-class.md#movefirst)

1. Al último registro del conjunto de registros o al último conjunto de filas: llame a la [MoveLast](../../mfc/reference/crecordset-class.md#movelast) función miembro.

1. *N* registros relativos a la posición actual: llame a la [Move](../../mfc/reference/crecordset-class.md#move) función miembro.

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Para probar el final o el principio del conjunto de registros

1. ¿Has pasado el último registro? Llame a la [isEOF](../../mfc/reference/crecordset-class.md#iseof) función miembro.

1. ¿Se ha desplazado por delante del primer registro (moviéndose hacia atrás)? Llame a la [isBOF](../../mfc/reference/crecordset-class.md#isbof) función miembro.

En el ejemplo `IsBOF` `IsEOF` de código siguiente se utiliza y para detectar los límites de un conjunto de registros al desplazarse en cualquier dirección.

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

`IsEOF`devuelve un valor distinto de cero si el conjunto de registros se coloca más allá del último registro. `IsBOF`devuelve un valor distinto de cero si el conjunto de registros se coloca por delante del primer registro (antes de todos los registros). En cualquier caso, no hay ningún registro actual en el que operar. Si llama `MovePrev` `IsBOF` a when ya `IsEOF` es TRUE o llama `CDBException`cuando `MoveNext` ya es TRUE, el marco de trabajo produce un archivo . También puede `IsBOF` usar `IsEOF` y comprobar si hay un conjunto de registros vacío.

Para obtener más información acerca de la navegación de conjuntos de registros, vea [Conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>Cuando se admite el desplazamiento

Como se diseñó originalmente, SQL solo proporciona el desplazamiento hacia delante, pero ODBC amplía las capacidades de desplazamiento. El nivel de compatibilidad disponible para el desplazamiento depende de los controladores ODBC con los que funciona la aplicación, el nivel de conformidad de la API ODBC del controlador y si la biblioteca de cursores ODBC se carga en la memoria. Para obtener más información, vea [ODBC](../../data/odbc/odbc-basics.md) y [ODBC: la biblioteca](../../data/odbc/odbc-the-odbc-cursor-library.md)de cursores ODBC .

> [!TIP]
> Puede controlar si se utiliza la biblioteca de cursores. Vea los parámetros *bUseCursorLib* y *dwOptions* en [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
> A diferencia de las clases DAO de MFC, las clases ODBC de MFC no proporcionan un conjunto de `Find` funciones para localizar el registro siguiente (o anterior) que cumple los criterios especificados.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Conjunto de registros: Filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
