---
title: "Determinar dinámicamente las columnas se devuelve al consumidor | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: da3d6e700ef69bda084a6bc5c010957c7fddd0c4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>Determinar dinámicamente las columnas que se devuelven al consumidor
Normalmente, las macros PROVIDER_COLUMN_ENTRY controlan la **IColumnsInfo:: GetColumnsInfo** llamar. Sin embargo, dado que un consumidor puede decidir utilizar marcadores, el proveedor debe poder cambiar las columnas devueltas dependiendo de si el consumidor solicita un marcador.  
  
 Para controlar la **IColumnsInfo:: GetColumnsInfo** llamada, elimine PROVIDER_COLUMN_MAP, que define una función `GetColumnInfo`, desde la `CAgentMan` usuario registro en MyProviderRS.h y reemplácela con la definición para su propio `GetColumnInfo` (función):  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
class CAgentMan  
{  
public:  
   DWORD dwBookmark;  
   TCHAR szCommand[256];  
   TCHAR szText[256];  
   TCHAR szCommand2[256];  
   TCHAR szText2[256];  
  
   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);  
   bool operator==(const CAgentMan& am)  
   {  
      return (lstrcmpi(szCommand, am.szCommand) == 0);  
   }  
  
};  
```  
  
 A continuación, implementará la `GetColumnInfo` funcionando en MyProviderRS.cpp, como se muestra en el código siguiente.  
  
 `GetColumnInfo` comprueba primero si la propiedad de OLE DB **DBPROP_BOOKMARKS** se establece. Para obtener la propiedad `GetColumnInfo` utiliza un puntero (`pRowset`) para el objeto de conjunto de filas. El `pThis` puntero representa la clase que creó el conjunto de filas, que es la clase donde se almacena la asignación de propiedad. `GetColumnInfo` conversiones de tipo el `pThis` puntero a un `RMyProviderRowset` puntero.  
  
 Para comprobar si la **DBPROP_BOOKMARKS** propiedad, `GetColumnInfo` utiliza la `IRowsetInfo` interfaz, que puede obtener mediante una llamada a `QueryInterface` en el `pRowset` interfaz. Como alternativa, puede usar un ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md) método en su lugar.  
  
```cpp
////////////////////////////////////////////////////////////////////  
// MyProviderRS.cpp  
ATLCOLUMNINFO* CAgentMan::GetColumnInfo(void* pThis, ULONG* pcCols)  
{  
   static ATLCOLUMNINFO _rgColumns[5];  
   ULONG ulCols = 0;  
  
   // Check the property flag for bookmarks; if it is set, set the zero   
   // ordinal entry in the column map with the bookmark information.  
   CAgentRowset* pRowset = (CAgentRowset*) pThis;  
   CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;  
  
   CDBPropIDSet set(DBPROPSET_ROWSET);  
   set.AddPropertyID(DBPROP_BOOKMARKS);  
   DBPROPSET* pPropSet = NULL;  
   ULONG ulPropSet = 0;  
   HRESULT hr;  
  
   if (spRowsetProps)  
      hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);  
  
   if (pPropSet)  
   {  
      CComVariant var = pPropSet->rgProperties[0].vValue;  
      CoTaskMemFree(pPropSet->rgProperties);  
      CoTaskMemFree(pPropSet);  
  
      if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))  
      {  
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),   
         DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,   
         DBCOLUMNFLAGS_ISBOOKMARK)  
         ulCols++;  
      }  
   }  
  
   // Next, set the other columns up.  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szCommand)  
   ulCols++;  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szText)  
   ulCols++;  
  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szCommand2)  
   ulCols++;  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szText2)  
   ulCols++;  
  
   if (pcCols != NULL)  
      *pcCols = ulCols;  
  
   return _rgColumns;  
}  
```  
  
 Este ejemplo utiliza una matriz estática para contener la información de columna. Si el consumidor no desea que la columna de marcador, se utiliza con una entrada de la matriz. Para controlar la información, cree dos macros de matriz: ADD_COLUMN_ENTRY y ADD_COLUMN_ENTRY_EX. ADD_COLUMN_ENTRY_EX utiliza un parámetro adicional, `flags`, que es necesario para designar una columna de marcador.  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = 0; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);  
  
#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member, flags) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = flags; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member); \  
   memset(&(_rgColumns[ulCols].columnid), 0, sizeof(DBID)); \  
   _rgColumns[ulCols].columnid.uName.pwszName = (LPOLESTR)name;  
```  
  
 En el `GetColumnInfo` función, la macro de marcador se usa como el siguiente:  
  
```  
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),  
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,   
   DBCOLUMNFLAGS_ISBOOKMARK)  
```  
  
 Ahora puede compilar y ejecutar el proveedor mejorado. Para probar el proveedor, modifique el consumidor de prueba como se describe en [implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md). Ejecute el consumidor de prueba con el proveedor. Compruebe que el consumidor de prueba recupera las cadenas apropiadas del proveedor al hacer clic en el **ejecutar** botón en el **consumidor de prueba** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Mejorar un proveedor sencillo de solo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)