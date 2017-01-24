---
title: "Determinar din&#225;micamente las columnas que se devuelven al consumidor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marcadores [C++], determinación dinámica de columnas"
  - "determinar columnas dinámicamente [C++]"
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Determinar din&#225;micamente las columnas que se devuelven al consumidor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Normalmente, las macros PROVIDER\_COLUMN\_ENTRY controlan la llamada a **IColumnsInfo::GetColumnsInfo**.  Sin embargo, dado que un consumidor puede decidir utilizar marcadores, el proveedor debe poder cambiar las columnas que se devuelven, en función de si el consumidor solicita un marcador.  
  
 Para controlar la llamada a **IColumnsInfo::GetColumnsInfo**, elimine PROVIDER\_COLUMN\_MAP, que define una función `GetColumnInfo`, del registro de usuario `CAgentMan` de MyProviderRS.h y reemplácela con la definición de su propia función `GetColumnInfo`:  
  
```  
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
  
 A continuación, implemente la función `GetColumnInfo` en MyProviderRS.cpp, como se muestra en el siguiente fragmento de código.  
  
 `GetColumnInfo` comprueba en primer lugar si el valor de la propiedad **DBPROP\_BOOKMARKS** de OLE DB está establecido.  Para obtener la propiedad, `GetColumnInfo` utiliza un puntero \(`pRowset`\) al objeto de conjunto de filas.  El puntero `pThis` representa la clase que creó el conjunto de filas, que es la clase en la que está almacenado el mapa de propiedades.  `GetColumnInfo` convierte el tipo del puntero `pThis` al de un puntero `RMyProviderRowset`.  
  
 Para comprobar el valor de la propiedad **DBPROP\_BOOKMARKS**, `GetColumnInfo` utiliza la interfaz `IRowsetInfo`, que se puede obtener llamando a `QueryInterface` en la interfaz `pRowset`.  Como alternativa, puede utilizar un método [CComQIPtr](../../atl/reference/ccomqiptr-class.md) de ATL.  
  
```  
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
  
 En este ejemplo se utiliza una matriz estática para que contenga la información de columna.  Si el consumidor no desea la columna de marcador, habrá una entrada de matriz no utilizada.  Para controlar la información, debe crear dos macros de matriz: ADD\_COLUMN\_ENTRY y ADD\_COLUMN\_ENTRY\_EX.  ADD\_COLUMN\_ENTRY\_EX utiliza un parámetro adicional, `flags`, que es necesario para designar una columna de marcador.  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision,   
scale, guid, dataClass, member) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = 0; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);  
  
#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type,   
precision, scale, guid, dataClass, member, flags) \  
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
  
 En la función `GetColumnInfo`, se utiliza la macro de marcador de la manera siguiente:  
  
```  
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),  
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,   
   DBCOLUMNFLAGS_ISBOOKMARK)  
```  
  
 Ahora puede compilar y ejecutar el proveedor mejorado.  Para probar el proveedor, modifique el consumidor de prueba como se describe en [Implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md).  Ejecute el consumidor de prueba con el proveedor.  Compruebe que el consumidor de prueba recupera las cadenas apropiadas del proveedor cuando haga clic en el botón **Ejecutar** en el cuadro de diálogo **Consumidor de prueba**.  
  
## Vea también  
 [Mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)