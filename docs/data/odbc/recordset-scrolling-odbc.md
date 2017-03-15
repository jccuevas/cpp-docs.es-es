---
title: "Conjunto de registros: Desplazamiento (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Move (método de conjuntos de registros)"
  - "navegación [C++], conjuntos de registros"
  - "conjuntos de registros ODBC, desplazarse"
  - "conjuntos de registros [C++], principio"
  - "conjuntos de registros [C++], final de"
  - "conjuntos de registros [C++], moverse entre registros"
  - "conjuntos de registros [C++], navegar"
  - "desplazarse [C++], conjuntos de registros"
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Conjunto de registros: Desplazamiento (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Después de abrir un conjunto de registros, es necesario tener acceso a los registros para mostrar valores, efectuar cálculos, generar informes, etc.  El desplazamiento permite moverse de un registro a otro en el conjunto de registros.  
  
 En este tema se explica:  
  
-   [Cómo desplazarse de un registro a otro en un conjunto de registros](#_core_scrolling_from_one_record_to_another).  
  
-   [Circunstancias en las que el desplazamiento es o no compatible](#_core_when_scrolling_is_supported).  
  
##  <a name="_core_scrolling_from_one_record_to_another"></a> Desplazarse de un registro a otro  
 La clase `CRecordset` proporciona las funciones miembro **Move** para desplazarse en un conjunto de registros.  Estas funciones mueven el registro actual por conjuntos de filas.  Si se implementó la obtención de filas masiva, una operación **Move** reajusta la posición del conjunto de registros según el tamaño del conjunto de filas.  Si no se implementó la obtención masiva de filas, una llamada a una función **Move** reajusta la posición del conjunto de registros de registro en registro.  Para obtener más información sobre la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Al desplazarse por un conjunto de registros, es posible que no se omitan los registros eliminados.  Para obtener más información, vea la función miembro [IsDeleted](../Topic/CRecordset::IsDeleted.md).  
  
 Además de las funciones **Move**, `CRecordset` proporciona funciones miembro para comprobar si se alcanzó el final o el comienzo del conjunto de registros.  
  
 Para determinar si es posible el desplazamiento en un conjunto de registros, llame a la función miembro `CanScroll`.  
  
#### Para desplazarse  
  
1.  Hacia delante un registro o un conjunto de filas: llame a la función miembro [MoveNext](../Topic/CRecordset::MoveNext.md).  
  
2.  Hacia atrás un registro o un conjunto de filas: llame a la función miembro [MovePrev](../Topic/CRecordset::MovePrev.md).  
  
3.  Al primer registro del conjunto de registros: llame a la función miembro [MoveFirst](../Topic/CRecordset::MoveFirst.md).  
  
4.  Al último registro del conjunto de registros o al último conjunto de filas: llame a la función miembro [MoveLast](../Topic/CRecordset::MoveLast.md).  
  
5.  *N* registros respecto a la posición actual: llame a la función miembro [Move](../Topic/CRecordset::Move.md).  
  
#### Para probar si se ha alcanzado el final o el comienzo del conjunto de registros  
  
1.  ¿Se ha desplazado más allá del último registro?  Llame a la función miembro [IsEOF](../Topic/CRecordset::IsEOF.md).  
  
2.  ¿Se ha desplazado más allá del primer registro \(moviéndose hacia atrás\)?  Llame a la función miembro [IsBOF](../Topic/CRecordset::IsBOF.md).  
  
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
  
 `IsEOF` devuelve un valor distinto de cero si el conjunto de registros está colocado detrás del último registro.  `IsBOF` devuelve un valor distinto de cero si el conjunto de registros está colocado delante del primer registro \(antes de todos los registros\).  En cualquier caso, no hay un registro actual sobre el cual trabajar.  Si se llama a `MovePrev` cuando `IsBOF` ya es **TRUE**, o se llama a `MoveNext` cuando `IsEOF` ya es **TRUE**, el marco de trabajo produce una excepción `CDBException`.  También se puede usar `IsBOF` y `IsEOF` para comprobar la existencia de conjuntos de registros vacíos.  
  
 Para obtener más información sobre la navegación por conjuntos de registros, vea [Conjunto de registros: Marcadores y posiciones absolutas \(ODBC\)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="_core_when_scrolling_is_supported"></a> Cuando se admite el desplazamiento  
 Según su diseño original, SQL proporcionaba sólo desplazamiento hacia delante, pero ODBC extiende las capacidades de desplazamiento.  El nivel disponible de compatibilidad con desplazamiento depende de los controladores ODBC con los que funcione la aplicación, el nivel de conformidad del controlador con la API de ODBC y de si está cargada en memoria la biblioteca de cursores ODBC.  Para obtener más información, vea [ODBC](../../data/odbc/odbc-basics.md) y [ODBC: Biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!TIP]
>  Se puede controlar si se utiliza la biblioteca de cursores.  Vea los parámetros `bUseCursorLib` y `dwOptions` de [CDatabase::Open](../Topic/CDatabase::Open.md).  
  
> [!NOTE]
>  A diferencia de las clases DAO de MFC, las clases ODBC de MFC no proporcionan ningún conjunto de funciones de **búsqueda** para buscar el registro siguiente \(o anterior\) que cumpla unos criterios específicos.  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::CanScroll](../Topic/CRecordset::CanScroll.md)   
 [CRecordset::CheckRowsetError](../Topic/CRecordset::CheckRowsetError.md)   
 [Conjunto de registros: Filtrar registros \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)