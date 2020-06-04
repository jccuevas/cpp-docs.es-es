---
title: Determinar dinámicamente las columnas que se devuelven al consumidor
ms.date: 10/26/2018
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
ms.openlocfilehash: 6b6061fc7da6f4c4dd53ae70a0e2d5ba7ec40023
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079645"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>Determinar dinámicamente las columnas que se devuelven al consumidor

Normalmente, las macros PROVIDER_COLUMN_ENTRY controlan la llamada `IColumnsInfo::GetColumnsInfo`. Sin embargo, dado que un consumidor puede optar por usar marcadores, el proveedor debe ser capaz de cambiar las columnas devueltas en función de si el consumidor solicita un marcador.

Para controlar la llamada `IColumnsInfo::GetColumnsInfo`, elimine el PROVIDER_COLUMN_MAP, que define una función `GetColumnInfo`, del registro de usuario `CCustomWindowsFile` en RS. h *personalizado*y reemplácelo por la definición de su propia función `GetColumnInfo`:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H
class CCustomWindowsFile
{
public:
   DWORD dwBookmark;
   static const int iSize = 256;
   TCHAR szCommand[iSize];
   TCHAR szText[iSize];
   TCHAR szCommand2[iSize];
   TCHAR szText2[iSize];
  
   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
   bool operator==(const CCustomWindowsFile& am)
   {
      return (lstrcmpi(szCommand, am.szCommand) == 0);
   }
};
```

A continuación, implemente la función `GetColumnInfo` en RS. cpp *personalizado*, tal y como se muestra en el código siguiente.

`GetColumnInfo` comprueba en primer lugar si se establece la propiedad OLE DB `DBPROP_BOOKMARKS`. Para obtener la propiedad, `GetColumnInfo` usa un puntero (`pRowset`) al objeto de conjunto de filas. El puntero `pThis` representa la clase que creó el conjunto de filas, que es la clase donde se almacena la asignación de propiedades. `GetColumnInfo` conversiones el puntero de `pThis` a un puntero de `RCustomRowset`.

Para comprobar la propiedad `DBPROP_BOOKMARKS`, `GetColumnInfo` utiliza la interfaz `IRowsetInfo`, que puede obtener llamando a `QueryInterface` en la interfaz `pRowset`. Como alternativa, puede usar en su lugar un método [CComQIPtr](../../atl/reference/ccomqiptr-class.md) de ATL.

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp
ATLCOLUMNINFO* CCustomWindowsFile::GetColumnInfo(void* pThis, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;
  
   // Check the property flag for bookmarks; if it is set, set the zero
   // ordinal entry in the column map with the bookmark information.
   CCustomRowset* pRowset = (CCustomRowset*) pThis;
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
         DBTYPE_BYTES, 0, 0, GUID_NULL, CCustomWindowsFile, dwBookmark,
         DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }
  
   // Next, set the other columns up.
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CCustomWindowsFile, szCommand)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CCustomWindowsFile, szText)
   ulCols++;
  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CCustomWindowsFile, szCommand2)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CCustomWindowsFile, szText2)
   ulCols++;
  
   if (pcCols != NULL)
      *pcCols = ulCols;
  
   return _rgColumns;
}
```

En este ejemplo se usa una matriz estática para almacenar la información de la columna. Si el consumidor no desea la columna de marcador, una entrada de la matriz no se utiliza. Para controlar la información, cree dos macros de matriz: ADD_COLUMN_ENTRY y ADD_COLUMN_ENTRY_EX. ADD_COLUMN_ENTRY_EX toma un parámetro adicional, *Flags*, que es necesario si designa una columna de marcador.

```cpp
////////////////////////////////////////////////////////////////////////  
// CustomRS.h  
  
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

En la función `GetColumnInfo`, la macro Bookmark se usa de la siguiente manera:

```cpp
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
   DBCOLUMNFLAGS_ISBOOKMARK)
```

Ahora puede compilar y ejecutar el proveedor mejorado. Para probar el proveedor, modifique el consumidor de prueba tal y como se describe en [implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md). Ejecute el consumidor de prueba con el proveedor y compruebe que el consumidor de prueba recupera las cadenas adecuadas del proveedor.

## <a name="see-also"></a>Consulte también

[Mejorar un proveedor sencillo de solo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
