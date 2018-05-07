---
title: 'Conjunto de registros: Desplazamiento (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 19058ec3d9a7840fc0e90be84f2734c49f2c8e85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-scrolling-odbc"></a>Conjunto de registros: Desplazamiento (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Después de abrir un conjunto de registros, necesita para tener acceso a los registros para mostrar valores, realizar cálculos, generar informes y así sucesivamente. El desplazamiento permite que desplazarse por los registros por el conjunto de registros.  
  
 En este tema se explica:  
  
-   [Cómo desplazarse de un registro a otro en un conjunto de registros](#_core_scrolling_from_one_record_to_another).  
  
-   [En qué circunstancias desplazamiento es y no se admite](#_core_when_scrolling_is_supported).  
  
##  <a name="_core_scrolling_from_one_record_to_another"></a> Desplazamiento de un registro a otro  
 Clase `CRecordset` proporciona el **mover** funciones miembro para desplazarse dentro de un conjunto de registros. Estas funciones mueven el registro actual por conjuntos de filas. Si ha implementado la obtención masiva de filas, una **mover** operación cambia de posición el conjunto de registros por el tamaño del conjunto de filas. Si no ha implementado de filas masiva de filas, una llamada a un **mover** función cambia de posición el conjunto de registros mediante un único registro cada vez. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Al desplazarse por un conjunto de registros, registros eliminados no se puede omitir. Para obtener más información, consulte el [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) función miembro.  
  
 Además el **mover** funciones, `CRecordset` proporciona funciones miembro para comprobar si se ha desplazado más allá del final o el comienzo del conjunto de registros.  
  
 Para determinar si el desplazamiento es posible en el conjunto de registros, llame a la `CanScroll` función miembro.  
  
#### <a name="to-scroll"></a>Para desplazarse  
  
1.  Reenviar un registro o un conjunto de filas: llame a la [MoveNext](../../mfc/reference/crecordset-class.md#movenext) función miembro.  
  
2.  Hacia atrás un registro o un conjunto de filas: llame a la [MovePrev](../../mfc/reference/crecordset-class.md#moveprev) función miembro.  
  
3.  En el primer registro del conjunto de registros: llame a la [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) función miembro.  
  
4.  En el último registro en el conjunto de registros o al último conjunto de filas: llame a la [MoveLast](../../mfc/reference/crecordset-class.md#movelast) función miembro.  
  
5.  *N* registros con respecto a la posición actual: llame a la [mover](../../mfc/reference/crecordset-class.md#move) función miembro.  
  
#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Para comprobar el final o al principio del conjunto de registros  
  
1.  ¿Se ha desplazado más allá del último registro? Llame a la [IsEOF](../../mfc/reference/crecordset-class.md#iseof) función miembro.  
  
2.  ¿Se ha desplazado delante del primer registro (mover hacia atrás)? Llame a la [IsBOF](../../mfc/reference/crecordset-class.md#isbof) función miembro.  
  
 El siguiente ejemplo de código usa `IsBOF` y `IsEOF` para detectar los límites de un conjunto de registros al desplazarse en cualquier dirección.  
  
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
  
 `IsEOF` Devuelve un valor distinto de cero si el conjunto de registros está colocado más allá del último registro. `IsBOF` Devuelve un valor distinto de cero si el conjunto de registros se coloca delante del primer registro (antes de todos los registros). En cualquier caso, no hay ningún registro actual para operar en. Si se llama a `MovePrev` cuando `IsBOF` ya está **TRUE** o llamar a `MoveNext` cuando `IsEOF` ya está **TRUE**, el marco de trabajo produce una `CDBException`. También puede usar `IsBOF` y `IsEOF` para comprobar si un conjunto de registros vacío.  
  
 Para obtener más información sobre la navegación de conjunto de registros, vea [conjunto de registros: marcadores y posiciones absolutas (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="_core_when_scrolling_is_supported"></a> Cuando se admite el desplazamiento  
 Según su diseño original, SQL proporcionaba sólo desplazamiento hacia delante, pero ODBC extiende las funciones de desplazamiento. El nivel disponible de compatibilidad con desplazamiento depende de los controladores ODBC que la aplicación funcione con nivel de conformidad de API de ODBC de su controlador, y si la biblioteca de cursores ODBC se carga en memoria. Para obtener más información, consulte [ODBC](../../data/odbc/odbc-basics.md) y [ODBC: biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!TIP]
>  Puede controlar si se utiliza la biblioteca de cursores. Consulte la `bUseCursorLib` y `dwOptions` parámetros [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open).  
  
> [!NOTE]
>  A diferencia de las clases DAO de MFC, las clases ODBC de MFC no proporcionan un conjunto de **buscar** funciones para buscar el registro siguiente (o anterior) que cumpla los criterios especificados.  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)   
 [CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)   
 [Conjunto de registros: Filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)