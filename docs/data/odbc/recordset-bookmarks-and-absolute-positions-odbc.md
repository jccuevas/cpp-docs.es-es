---
title: "Conjunto de registros: Marcadores y posiciones absolutas (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetAbsolutePosition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "posiciones absolutas, conjuntos de registros ODBC"
  - "marcadores"
  - "marcadores, CDBVariant"
  - "marcadores, conjuntos de registros ODBC"
  - "CDBVariant (clase), marcadores"
  - "cursores [ODBC], posiciones absolutas en conjuntos de registros"
  - "GetBookmark (método)"
  - "conjuntos de registros ODBC, posiciones absolutas"
  - "conjuntos de registros ODBC, marcadores"
  - "ubicar registros"
  - "posición de registros"
  - "conjuntos de registros, posiciones absolutas"
  - "conjuntos de registros, marcadores"
  - "SetAbsolutePosition (método)"
  - "SetAbsolutePosition (método), marcadores"
  - "SetBookmark (método)"
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Conjunto de registros: Marcadores y posiciones absolutas (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Al navegar por un conjunto de registros, a menudo es necesaria una forma de regresar a un registro determinado.  El marcador y la posición absoluta de un registro proporcionan dos métodos para tal fin.  
  
 En este tema se explica:  
  
-   [Cómo usar los marcadores](#_core_bookmarks_in_mfc_odbc).  
  
-   [Cómo establecer el registro actual usando posiciones absolutas](#_core_absolute_positions_in_mfc_odbc).  
  
##  <a name="_core_bookmarks_in_mfc_odbc"></a> Marcadores en ODBC de MFC  
 Un marcador identifica de forma exclusiva a un registro.  Al navegar por un conjunto de registros, no siempre se puede confiar en la posición absoluta de un registro, dado que éstos pueden eliminarse del conjunto de registros.  La forma más segura de conservar la posición de un registro es utilizar su correspondiente marcador.  La clase `CRecordset` proporciona funciones miembro para:  
  
-   Obtener el marcador del registro actual, para que se pueda guardar en una variable \([GetBookmark](../Topic/CRecordset::GetBookmark.md)\).  
  
-   Desplazarse con rapidez a un registro dado especificando su marcador, guardado previamente en una variable \([SetBookmark](../Topic/CRecordset::SetBookmark.md)\).  
  
 El siguiente ejemplo muestra cómo utilizar dichas funciones miembro para marcar el registro actual y regresar más tarde al mismo:  
  
```  
// rs is a CRecordset or  
// CRecordset-derived object  
  
CDBVariant varRecordToReturnTo;  
rs.GetBookmark( varRecordToReturnTo );  
  
// More code in which you  
// move to other records  
  
rs.SetBookmark( varRecordToReturnTo );  
```  
  
 No es necesario extraer el tipo de datos subyacente del objeto [CDBVariant Class](../../mfc/reference/cdbvariant-class.md).  Asigne valor mediante `GetBookmark` y regrese al marcador con `SetBookmark`.  
  
> [!NOTE]
>  Según el controlador ODBC y el tipo de conjunto de registros, puede que no se admita el uso de marcadores.  Se puede determinar con facilidad si se admiten los marcadores llamando a [CRecordset::CanBookmark](../Topic/CRecordset::CanBookmark.md).  Aun más, si se admite el uso de marcadores, se deben elegir explícitamente para implementarlos especificando la opción **CRecordset::useBookmarks** en la función miembro [CRecordset::Open](../Topic/CRecordset::Open.md).  También se debe comprobar la persistencia de los marcadores después de ciertas operaciones con conjuntos de registros.  Por ejemplo, si se ejecuta **Requery** en un conjunto de registros, puede que los marcadores ya no sean válidos.  Llame a [CDatabase::GetBookmarkPersistence](../Topic/CDatabase::GetBookmarkPersistence.md) para comprobar si puede llamar sin ningún riesgo a `SetBookmark`.  
  
##  <a name="_core_absolute_positions_in_mfc_odbc"></a> Posiciones absolutas en ODBC de MFC  
 Además de los marcadores, la clase `CRecordset` permite establecer el registro actual especificando una posición ordinal.  Esto se denomina colocación absoluta.  
  
> [!NOTE]
>  La colocación absoluta no está disponible en conjuntos de registros sólo hacia delante.  Para obtener más información sobre conjuntos de registros solo hacia delante, vea [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md).  
  
 Para mover el puntero de registro actual mediante la posición absoluta, haga una llamada a [CRecordset::SetAbsolutePosition](../Topic/CRecordset::SetAbsolutePosition.md).  Al pasar un valor a `SetAbsolutePosition`, el registro correspondiente a esa posición ordinal se convierte en el registro actual.  
  
> [!NOTE]
>  La posición absoluta de un registro no es potencialmente fiable.  Si el usuario elimina registros del conjunto de registros, cambia la posición ordinal de los registros posteriores.  Los marcadores son el método recomendado para mover el registro actual.  Para obtener más información, vea [Marcadores en ODBC de MFC](#_core_bookmarks_in_mfc_odbc).  
  
 Para obtener más información sobre navegación en conjuntos de registros, vea [Conjunto de registros: Desplazamiento \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md).  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)