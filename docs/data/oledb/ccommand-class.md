---
title: "CCommand (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CCommand"
  - "CCommand"
  - "ATL.CCommand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCommand (clase)"
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CCommand (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona métodos para establecer y ejecutar un comando.  
  
## Sintaxis  
  
```  
template <  
   class TAccessor = CNoAccessor,  
   template < typename T > class TRowset = CRowset,  
   class TMultiple = CNoMultipleResults   
>  
class CCommand :   
   public CAccessorRowset <  
      TAccessor,   
      TRowset   
   >,  
   public CCommandBase,  
   public TMultiple  
```  
  
#### Parámetros  
 `TAccessor`  
 El tipo de clase de descriptor de acceso \(como `CDynamicParameterAccessor`, `CDynamicStringAccessor`, o `CEnumeratorAccessor`\) que desea que el comando de utilizar.  El valor predeterminado es `CNoAccessor`, que especifica que los parámetros de la clase o columnas no admiten la salida.  
  
 `TRowset`  
 El tipo de clase de conjunto de filas \(como `CArrayRowset` o `CNoRowset`\) que desea que el comando de utilizar.  El valor predeterminado es `CRowset`.  
  
 `TMultiple`  
 Para utilizar un comando OLE DB que puede devolver varios resultados, especifique [CMultipleResults](../../data/oledb/cmultipleresults-class.md).  Si no, utilice [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md).  Para obtener información detallada, vea [IMultipleResults](https://msdn.microsoft.com/en-us/library/ms721289.aspx).  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[Cerrar](../../data/oledb/ccommand-close.md)|Cierre el comando actual.|  
|[GetNextResult](../../data/oledb/ccommand-getnextresult.md)|Captura el resultado siguiente al utilizar varios conjuntos de resultados.|  
|[Abrir](../../data/oledb/ccommand-open.md)|Ejecuta y enlaza opcionalmente el comando.|  
  
### Métodos heredados  
  
|||  
|-|-|  
|[Create](../../data/oledb/ccommand-create.md)|Crea un nuevo comando para la sesión especificada, establezca el texto de comando.|  
|[CreateCommand](../../data/oledb/ccommand-createcommand.md)|Crea un nuevo comando.|  
|[GetParameterInfo](../../data/oledb/ccommand-getparameterinfo.md)|Obtiene una lista de parámetros del comando, sus nombres, y sus tipos.|  
|[Preparación](../../data/oledb/ccommand-prepare.md)|Valida y optimiza el comando actual.|  
|[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)|Libera el descriptor de parámetros en caso necesario, continuación libera el comando.|  
|[SetParameterInfo](../../data/oledb/ccommand-setparameterinfo.md)|Especifica el tipo nativo de cada parámetro de comando.|  
|[Unprepare](../../data/oledb/ccommand-unprepare.md)|Descarta el plan de ejecución actual del comando.|  
  
## Comentarios  
 Utilice esta clase cuando necesite realizar una operación basada en parámetros o ejecutar un comando  Si sólo tiene que abrir un conjunto de filas, utilice [CTable](../../data/oledb/ctable-class.md) en su lugar.  
  
 La clase de descriptor de acceso que usa determina el método de enlazar parámetros y datos.  
  
 Tenga en cuenta que no puede utilizar procedimientos almacenados con el proveedor OLE DB para Jet porque ese proveedor no admite procedimientos almacenados \(sólo se permiten constantes en cadenas de consulta\).  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)