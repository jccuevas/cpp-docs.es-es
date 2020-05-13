---
title: 'Conjunto de registros: Marcadores y posiciones absolutas (ODBC)'
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
ms.openlocfilehash: 77c8bbaf7c0bc21dab62c3785364e72656287815
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367066"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Conjunto de registros: Marcadores y posiciones absolutas (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Al navegar por un conjunto de registros, a menudo necesita una forma de volver a un registro determinado. El marcador y la posición absoluta de un registro proporcionan dos métodos de este tipo.

En este tema se explica:

- [Cómo utilizar marcadores](#_core_bookmarks_in_mfc_odbc).

- [Cómo establecer el registro actual utilizando posiciones absolutas](#_core_absolute_positions_in_mfc_odbc).

## <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>Marcadores en MFC ODBC

Un marcador identifica de forma única un registro. Cuando navega por un conjunto de registros, no siempre puede confiar en la posición absoluta de un registro porque los registros se pueden eliminar del conjunto de registros. La forma fiable de realizar un seguimiento de la posición de un registro es utilizar su marcador. La `CRecordset` clase proporciona funciones miembro para:

- Obtener el marcador del registro actual, por lo que puede guardarlo en una variable ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Moverse rápidamente a un registro determinado especificando su marcador, que guardó anteriormente en una variable ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).

En el ejemplo siguiente se muestra cómo utilizar estas funciones miembro para marcar el registro actual y volver más adelante a él:

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

No es necesario extraer el tipo de datos subyacente del objeto [CDBVariant Class.](../../mfc/reference/cdbvariant-class.md) Asigne el `GetBookmark` valor con y `SetBookmark`vuelva a ese marcador con .

> [!NOTE]
> Según el controlador ODBC y el tipo de conjunto de registros, es posible que no se admitan marcadores. Puede determinar fácilmente si los marcadores son compatibles llamando a [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). Además, si se admiten marcadores, debe elegir explícitamente implementarlos especificando la `CRecordset::useBookmarks` opción en el [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) función miembro. También debe comprobar la persistencia de marcadores después de ciertas operaciones de conjunto de registros. Por ejemplo, `Requery` si un conjunto de registros, es posible que los marcadores ya no sean válidos. Llame a [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para comprobar `SetBookmark`si puede llamar de forma segura .

## <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>Posiciones absolutas en MFC ODBC

Además de `CRecordset` los marcadores, class le permite establecer el registro actual especificando una posición ordinal. Esto se denomina posicionamiento absoluto.

> [!NOTE]
> El posicionamiento absoluto no está disponible en conjuntos de registros de solo avance. Para obtener más información acerca de los conjuntos de registros de solo avance, vea [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md).

Para mover el puntero de registro actual mediante la posición absoluta, llame a [CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Cuando se pasa `SetAbsolutePosition`un valor a , el registro correspondiente a esa posición ordinal se convierte en el registro actual.

> [!NOTE]
> La posición absoluta de un registro es potencialmente poco fiable. Si el usuario elimina registros del conjunto de registros, cambia la posición ordinal de cualquier registro posterior. Los marcadores son el método recomendado para mover el registro actual. Para obtener más información, vea [Marcadores en ODBC de MFC](#_core_bookmarks_in_mfc_odbc).

Para obtener más información acerca de la navegación de conjuntos de registros, vea [Conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)
