---
title: "CRowset::FindNextRow | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CRowset.FindNextRow"
  - "CRowset<TAccessor>.FindNextRow"
  - "ATL::CRowset::FindNextRow"
  - "CRowset::FindNextRow"
  - "CRowset<TAccessor>::FindNextRow"
  - "CRowset.FindNextRow"
  - "ATL.CRowset<TAccessor>.FindNextRow"
  - "ATL::CRowset<TAccessor>::FindNextRow"
  - "FindNextRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FindNextRow (método)"
ms.assetid: 36484df9-3625-4f15-bf69-db73a8d91c55
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::FindNextRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encuentra la fila coincidente siguiente después del marcador especificado.  
  
## Sintaxis  
  
```  
  
      HRESULT FindNextRow(   
   DBCOMPAREOP op,   
   BYTE* pData,   
   DBTYPE wType,   
   DBLENGTH nLength,   
   BYTE bPrecision,   
   BYTE bScale,   
   BOOL bSkipCurrent = TRUE,   
   CBookmarkBase* pBookmark = NULL    
) throw( );  
```  
  
#### Parámetros  
 `op`  
 \[in\] La operación que se va comparar valores de fila.  Para los valores, vea [IRowsetFind::FindNextRow](https://msdn.microsoft.com/en-us/library/ms723091.aspx).  
  
 `pData`  
 \[in\] Un puntero al valor que se va a comparar.  
  
 `wType`  
 \[in\] Indica el tipo de datos de la parte del valor del búfer.  Para obtener información sobre las marcas de tipo, vea [Tipos de datos](https://msdn.microsoft.com/en-us/library/ms723969.aspx) en *la referencia del* programador de OLE [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `nLength`  
 \[in\] Longitud, en bytes, de la estructura de datos de consumidor asignada por el valor de datos.  Para obtener detalles, vea la descripción de **cbMaxLen** en [Estructuras de DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) en *la referencia del programador.*  
  
 `bPrecision`  
 \[in\] La precisión máxima utilizada para recopilar datos.  Sólo se utiliza si `wType` es `DBTYPE_NUMERIC`.  Para obtener más información, vea [Conversiones que implican DBTYPE\_NUMERIC o DBTYPE\_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx) en *la referencia del*programador.  
  
 `bScale`  
 \[in\] La escala utilizada para recopilar datos.  Sólo se utiliza si `wType` es `DBTYPE_NUMERIC` o **DBTYPE\_DECIMAL**.  Para obtener más información, vea [Conversiones que implican DBTYPE\_NUMERIC o DBTYPE\_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx) en *la referencia del*programador.  
  
 *bSkipCurrent*  
 \[in\] El número de filas de marcador en el que se va a iniciar una búsqueda.  
  
 `pBookmark`  
 \[in\] El marcador de posición en la que se va a iniciar una búsqueda.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método requiere la interfaz opcional **IRowsetFind**, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetFind** a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
 Para obtener información sobre cómo utilizar marca una dirección de la Internet en consumidores, vea [Mediante los marcadores](../../data/oledb/using-bookmarks.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [DBBINDING Structures](https://msdn.microsoft.com/en-us/library/ms716845.aspx)