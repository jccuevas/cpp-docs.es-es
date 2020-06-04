---
title: Compatibilidad del proveedor con los marcadores
ms.date: 11/04/2016
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
ms.openlocfilehash: e8ea949653c7e62f39ab9d1b181c419cf51fe3cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209838"
---
# <a name="provider-support-for-bookmarks"></a>Compatibilidad del proveedor con los marcadores

En el ejemplo de este tema se agrega la interfaz de `IRowsetLocate` a la clase `CCustomRowset`. En casi todos los casos, se empieza agregando una interfaz a un objeto COM existente. Después, puede probarlo agregando más llamadas desde las plantillas de consumidor. En el ejemplo se muestra cómo:

- Agregar una interfaz a un proveedor.

- Determinar dinámicamente las columnas que se van a devolver al consumidor.

- Agregar compatibilidad con marcadores.

La interfaz `IRowsetLocate` hereda de la interfaz `IRowset` . Para agregar la interfaz `IRowsetLocate`, herede `CCustomRowset` de [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md).

Agregar la interfaz `IRowsetLocate` es un poco diferente de la mayoría de las interfaces. Para que las VTABLEs estén alineadas, las plantillas de proveedor OLE DB tienen un parámetro de plantilla para controlar la interfaz derivada. En el código siguiente se muestra la nueva lista de herencia:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

// CCustomRowset
class CCustomRowset : public CRowsetImpl< CCustomRowset,
      CTextData, CCustomCommand, CAtlArray<CTextData>,
      CSimpleRow,
          IRowsetLocateImpl<CCustomRowset, IRowsetLocate>>
```

Se agregan los parámetros cuarto, quinto y sexto. En este ejemplo se usan los valores predeterminados para los parámetros cuarto y quinto, pero se especifica `IRowsetLocateImpl` como el sexto parámetro. `IRowsetLocateImpl` es una OLE DB clase de plantilla que toma dos parámetros de plantilla: enlazan la interfaz de `IRowsetLocate` a la clase `CCustomRowset`. Para agregar la mayoría de las interfaces, puede omitir este paso y pasar a la siguiente. Solo las interfaces `IRowsetLocate` y `IRowsetScroll` deben administrarse de esta manera.

A continuación, debe indicar al `CCustomRowset` que llame a `QueryInterface` para la interfaz de `IRowsetLocate`. Agregue la línea `COM_INTERFACE_ENTRY(IRowsetLocate)` al mapa. El mapa de interfaz para `CCustomRowset` debe aparecer como se muestra en el código siguiente:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

typedef CRowsetImpl< CCustomRowset, CTextData, CCustomCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CCustomRowset, IRowsetLocate>> _RowsetBaseClass;

BEGIN_COM_MAP(CCustomRowset)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

También debe enlazar la asignación a la clase `CRowsetImpl`. Agregue la macro COM_INTERFACE_ENTRY_CHAIN que se va a enlazar en el mapa de `CRowsetImpl`. Además, cree una definición de tipo llamada `RowsetBaseClass` que conste de la información de herencia. Esta definición de tipo es arbitraria y se puede omitir.

Por último, controle la llamada `IColumnsInfo::GetColumnsInfo`. Normalmente usaría el PROVIDER_COLUMN_ENTRY macros para hacerlo. Sin embargo, es posible que un consumidor quiera usar marcadores. Debe poder cambiar las columnas que devuelve el proveedor dependiendo de si el consumidor solicita un marcador.

Para controlar la llamada `IColumnsInfo::GetColumnsInfo`, elimine el mapa de PROVIDER_COLUMN en la clase `CTextData`. La macro PROVIDER_COLUMN_MAP define una función `GetColumnInfo`. Defina su propia `GetColumnInfo` función. La declaración de la función debe tener el siguiente aspecto:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H

class CTextData
{
   ...
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!
   static ATLCOLUMNINFO* GetColumnInfo(CCustomRowset* pThis,
        ULONG* pcCols);
   static ATLCOLUMNINFO* GetColumnInfo(CCustomCommand* pThis,
        ULONG* pcCols);
...
};
```

A continuación, implemente la función `GetColumnInfo` en el archivo RS. cpp *personalizado*como se indica a continuación:

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp

template <class TInterface>
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;

   CComQIPtr<TInterface> spProps = pPropsUnk;

   CDBPropIDSet set(DBPROPSET_ROWSET);
   set.AddPropertyID(DBPROP_BOOKMARKS);
   DBPROPSET* pPropSet = NULL;
   ULONG ulPropSet = 0;
   HRESULT hr;

   if (spProps)
      hr = spProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

   // Check the property flag for bookmarks, if it is set, set the
// zero ordinal entry in the column map with the bookmark
// information.

   if (pPropSet)
   {
      CComVariant var = pPropSet->rgProperties[0].vValue;
      CoTaskMemFree(pPropSet->rgProperties);
      CoTaskMemFree(pPropSet);

      if ((SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE)))
      {
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                     sizeof(DWORD), DBTYPE_BYTES,
            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                        DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }

   // Next set the other columns up.
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field1"), 1, 16, DBTYPE_STR,
          0xFF, 0xFF, GUID_NULL, CTextData, szField1)
   ulCols++;
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field2"), 2, 16, DBTYPE_STR,
       0xFF, 0xFF, GUID_NULL, CTextData, szField2)
   ulCols++;

   if (pcCols != NULL)
      *pcCols = ulCols;

   return _rgColumns;
}

ATLCOLUMNINFO* CTextData::GetColumnInfo(CCustomCommand* pThis,
     ULONG* pcCols)
{
   return CommonGetColInfo<ICommandProperties>(pThis->GetUnknown(),
        pcCols);
}

ATLCOLUMNINFO* CAgentMan::GetColumnInfo(RUpdateRowset* pThis, ULONG* pcCols)
{
   return CommonGetColInfo<IRowsetInfo>(pThis->GetUnknown(), pcCols);
}
```

`GetColumnInfo` primero comprueba si se ha establecido una propiedad denominada `DBPROP_IRowsetLocate`. OLE DB tiene propiedades para cada una de las interfaces opcionales del objeto de conjunto de filas. Si el consumidor desea utilizar una de estas interfaces opcionales, establece una propiedad en true. Después, el proveedor puede comprobar esta propiedad y realizar una acción especial basada en ella.

En la implementación de, obtiene la propiedad mediante el puntero al objeto de comando. El puntero `pThis` representa el conjunto de filas o la clase de comando. Dado que usa plantillas aquí, tiene que pasarlo como un puntero **void** o el código no se compila.

Especifique una matriz estática para almacenar la información de la columna. Si el consumidor no desea la columna de marcador, se desperdicia una entrada en la matriz. Puede asignar dinámicamente esta matriz, pero debe asegurarse de que la destruya correctamente. Este ejemplo define y utiliza las macros ADD_COLUMN_ENTRY y ADD_COLUMN_ENTRY_EX para insertar la información en la matriz. Puede Agregar las macros al RS *personalizado*. H, tal como se muestra en el código siguiente:

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

Para probar el código en el consumidor, debe realizar algunos cambios en el controlador de `OnRun`. El primer cambio en la función es que se agrega código para agregar una propiedad al conjunto de propiedades. El código establece la propiedad `DBPROP_IRowsetLocate` en true, lo que indica al proveedor que desea la columna de marcador. El código del controlador de `OnRun` debe aparecer de la siguiente manera:

```cpp
//////////////////////////////////////////////////////////////////////
// TestProv Consumer Application in TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

   if (source.Open("Custom.Custom.1", NULL, NULL, NULL,
          NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   CDBPropSet propset(DBPROPSET_ROWSET);
   propset.AddProperty(DBPROP_IRowsetLocate, true);
   if (table.Open(session, _T("c:\\public\\testprf2\\myData.txt"),
          &propset) != S_OK)
      return;

   CBookmark<4> tempBookmark;
   ULONG ulCount=0;
   while (table.MoveNext() == S_OK)
   {

      DBCOMPARE compare;
      if (ulCount == 2)
         tempBookmark = table.bookmark;

HRESULT hr = table.Compare(table.dwBookmark, table.dwBookmark,
                 &compare);
      if (FAILED(hr))
         ATLTRACE(_T("Compare failed: 0x%X\n"), hr);
      else
         _ASSERTE(compare == DBCOMPARE_EQ);

      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
      ulCount++;
   }

   table.MoveToBookmark(tempBookmark);
   m_ctlString1.AddString(table.szField1);
   m_ctlString2.AddString(table.szField2);
}
```

El bucle **While** contiene código para llamar al método `Compare` en la interfaz `IRowsetLocate`. El código que debe pasar siempre porque está comparando los mismos marcadores exactos. Además, almacene un marcador en una variable temporal para que pueda usarlo después de que el bucle **While** termine de llamar a la función `MoveToBookmark` en las plantillas de consumidor. La función `MoveToBookmark` llama al método `GetRowsAt` en `IRowsetLocate`.

También debe actualizar el registro de usuario en el consumidor. Agregue una entrada en la clase para controlar un marcador y una entrada en el COLUMN_MAP:

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

class CProvider
{
// Attributes
public:
   CBookmark<4>    bookmark;  // Add this line
   char   szCommand[16];
   char   szText[256];

   // Binding Maps
BEGIN_ACCESSOR_MAP(CProvider, 1)
   BEGIN_ACCESSOR(0, true)   // auto accessor
      BOOKMARK_ENTRY(bookmark)  // Add this line
      COLUMN_ENTRY(1, szField1)
      COLUMN_ENTRY(2, szField2)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

Cuando haya actualizado el código, debería poder compilar y ejecutar el proveedor con la interfaz `IRowsetLocate`.

## <a name="see-also"></a>Consulte también

[Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)
