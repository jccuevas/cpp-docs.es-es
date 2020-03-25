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
ms.openlocfilehash: 9a25c0fe4c1f08d376824fbc02211d22c7c14435
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212971"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Conjunto de registros: Marcadores y posiciones absolutas (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Al desplazarse por un conjunto de registros, a menudo necesita una forma de volver a un registro determinado. El marcador de un registro y la posición absoluta proporcionan dos métodos de este tipo.

En este tema se explica:

- [Cómo usar marcadores](#_core_bookmarks_in_mfc_odbc).

- [Cómo establecer el registro actual mediante posiciones absolutas](#_core_absolute_positions_in_mfc_odbc).

##  <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>Marcadores en ODBC de MFC

Un marcador identifica un registro de forma única. Cuando se navega por un conjunto de registros, no se puede confiar siempre en la posición absoluta de un registro porque los registros se pueden eliminar del conjunto de registros. La manera confiable de realizar un seguimiento de la posición de un registro es usar su marcador. La clase `CRecordset` proporciona funciones miembro para:

- Obtener el marcador del registro actual, por lo que se puede guardar en una variable ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Desplazarse rápidamente a un registro determinado especificando su marcador, que guardó anteriormente en una variable ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).

En el ejemplo siguiente se muestra cómo usar estas funciones miembro para marcar el registro actual y volver a él más adelante:

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

No es necesario extraer el tipo de datos subyacente del objeto de la [clase cdbvariant (](../../mfc/reference/cdbvariant-class.md) . Asigne el valor con `GetBookmark` y vuelva a ese marcador con `SetBookmark`.

> [!NOTE]
>  En función del tipo de conjunto de registros y del controlador ODBC, es posible que no se admitan marcadores. Puede determinar fácilmente si se admiten marcadores llamando a [CRecordset:: CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). Además, si se admiten marcadores, debe elegir explícitamente implementarlos especificando la opción `CRecordset::useBookmarks` en la función miembro [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) . También debe comprobar la persistencia de los marcadores después de ciertas operaciones de conjunto de registros. Por ejemplo, si `Requery` un conjunto de registros, es posible que los marcadores dejen de ser válidos. Llame a [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para comprobar si puede llamar a `SetBookmark`de forma segura.

##  <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>Posiciones absolutas en ODBC de MFC

Además de los marcadores, la clase `CRecordset` permite establecer el registro actual especificando una posición ordinal. Esto se denomina posicionamiento absoluto.

> [!NOTE]
>  La posición absoluta no está disponible en los conjuntos de registros solo hacia delante. Para obtener más información sobre los conjuntos de registros solo hacia delante, vea [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md).

Para mover el puntero del registro actual mediante la posición absoluta, llame a [CRecordset:: SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Cuando se pasa un valor a `SetAbsolutePosition`, el registro correspondiente a esa posición ordinal se convierte en el registro actual.

> [!NOTE]
>  La posición absoluta de un registro es potencialmente no confiable. Si el usuario elimina los registros del conjunto de registros, cambia la posición ordinal de cualquier registro subsiguiente. Los marcadores son el método recomendado para mover el registro actual. Para obtener más información, vea [marcadores en ODBC de MFC](#_core_bookmarks_in_mfc_odbc).

Para obtener más información sobre la navegación por conjuntos de registros, vea [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)
