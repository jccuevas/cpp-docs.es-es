---
title: 'CRowset:: FindNextRow | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset.FindNextRow
- CRowset<TAccessor>.FindNextRow
- ATL::CRowset::FindNextRow
- CRowset::FindNextRow
- CRowset<TAccessor>::FindNextRow
- CRowset.FindNextRow
- ATL.CRowset<TAccessor>.FindNextRow
- ATL::CRowset<TAccessor>::FindNextRow
- FindNextRow
dev_langs: C++
helpviewer_keywords: FindNextRow method
ms.assetid: 36484df9-3625-4f15-bf69-db73a8d91c55
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 08dd2a80040c4affb89b19dfff3b22103b4e9547
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetfindnextrow"></a>CRowset::FindNextRow
Busca la siguiente fila coincidente después del marcador especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `op`  
 [in] La operación que se utilizará en la comparación de valores de fila. Para los valores, vea [irowsetfind:: FindNextRow](https://msdn.microsoft.com/en-us/library/ms723091.aspx).  
  
 `pData`  
 [in] Un puntero al valor que se debe coincidir.  
  
 `wType`  
 [in] Indica el tipo de datos de la parte del valor del búfer. Para obtener información acerca de los indicadores de tipo, consulte [tipos de datos](https://msdn.microsoft.com/en-us/library/ms723969.aspx) en el *referencia del programador de OLE DB* del SDK de Windows.  
  
 `nLength`  
 [in] La longitud, en bytes, de la estructura de datos del consumidor asignada para el valor de datos. Para obtener más información, vea la descripción de **cbMaxLen** en [estructuras DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) en el *referencia del programador de OLE DB.*  
  
 `bPrecision`  
 [in] La precisión máxima que se utiliza al obtener datos. Sólo se usa si `wType` es `DBTYPE_NUMERIC`. Para obtener más información, consulte [las conversiones que involucran DBTYPE_NUMERIC o DBTYPE_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx) en el *referencia del programador de OLE DB*.  
  
 `bScale`  
 [in] La escala que se utiliza al obtener datos. Sólo se usa si `wType` es `DBTYPE_NUMERIC` o **DBTYPE_DECIMAL**. Para obtener más información, consulte [las conversiones que involucran DBTYPE_NUMERIC o DBTYPE_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx) en el *referencia del programador de OLE DB*.  
  
 *bSkipCurrent*  
 [in] El número de filas del marcador en el que se va a iniciar una búsqueda.  
  
 `pBookmark`  
 [in] El marcador de posición en la que se va a iniciar una búsqueda.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método requiere que la interfaz opcional **IRowsetFind**, que no se admite en todos los proveedores; si éste es el caso, el método devuelve **E_NOINTERFACE**. También debe establecer **DBPROP_IRowsetFind** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas.  
  
 Para obtener información sobre el uso de marcadores en los consumidores, consulte [Using Bookmarks](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (clase)](../../data/oledb/crowset-class.md)   
 [Estructuras DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)