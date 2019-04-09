---
title: Determinar dinámicamente las columnas que se devuelven al consumidor
ms.date: 10/26/2018
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
ms.openlocfilehash: 81353581d22f3d075fd19d783591ec856c21e241
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037664"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>Determinar dinámicamente las columnas que se devuelven al consumidor

Normalmente, las macros PROVIDER_COLUMN_ENTRY controlan la `IColumnsInfo::GetColumnsInfo` llamar. Sin embargo, dado que un consumidor puede optar por usar marcadores, el proveedor debe poder cambiar las columnas devueltas dependiendo de si el consumidor solicita un marcador.

Para controlar la `IColumnsInfo::GetColumnsInfo` llamada, elimine PROVIDER_COLUMN_MAP, que define una función `GetColumnInfo`, desde el `CCustomWindowsFile` registro de usuario en *personalizado*RS.h y reemplácela con la definición de sus propias `GetColumnInfo` función:

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

A continuación, implementará la `GetColumnInfo` funcionando en *personalizado*RS.cpp, tal como se muestra en el código siguiente.

`GetColumnInfo` comprueba primero si la propiedad OLE DB `DBPROP_BOOKMARKS` está establecido. Para obtener la propiedad, `GetColumnInfo` utiliza un puntero (`pRowset`) para el objeto de conjunto de filas. El `pThis` puntero representa la clase que crea el conjunto de filas, que es la clase donde se almacena la asignación de propiedad. `GetColumnInfo` conversiones de tipo el `pThis` puntero a un `RCustomRowset` puntero.

Para comprobar la `DBPROP_BOOKMARKS` propiedad `GetColumnInfo` usa el `IRowsetInfo` interfaz, que se puede obtener mediante una llamada a `QueryInterface` en el `pRowset` interfaz. Como alternativa, puede usar un ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md) método en su lugar.

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

Este ejemplo utiliza una matriz estática para contener la información de columna. Si el consumidor no desea que la columna de marcador, se utiliza con una entrada de la matriz. Para controlar la información, cree dos macros de matriz: ADD_COLUMN_ENTRY y ADD_COLUMN_ENTRY_EX. ADD_COLUMN_ENTRY_EX utiliza un parámetro adicional, *marcas*, que es necesario para designar una columna de marcador.

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

En el `GetColumnInfo` función, la macro de marcador se usa como esta:

```cpp
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
   DBCOLUMNFLAGS_ISBOOKMARK)
```

Ahora puede compilar y ejecutar el proveedor mejorado. Para probar el proveedor, modifique el consumidor de prueba como se describe en [implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md). Ejecute el consumidor de prueba con el proveedor y compruebe que el consumidor de prueba recupera las cadenas apropiadas del proveedor.

## <a name="see-also"></a>Vea también

[Mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
