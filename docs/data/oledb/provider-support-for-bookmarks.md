---
title: Compatibilidad del proveedor con los marcadores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 445aa5a2a609c3cf2da83e9ff876195a05a33d6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="provider-support-for-bookmarks"></a>Compatibilidad del proveedor con los marcadores
El ejemplo de este tema agrega la `IRowsetLocate` de la interfaz para la `CMyProviderRowset` clase. En casi todos casos, primero debe agregar una interfaz a un objeto COM existente. A continuación, puede probarlo agregando más llamadas de las plantillas de consumidor. El ejemplo se muestra cómo:  
  
-   Agregar una interfaz a un proveedor.  
  
-   Determinar dinámicamente las columnas que se devuelven al consumidor.  
  
-   Agregar compatibilidad con marcadores.  
  
 La interfaz `IRowsetLocate` hereda de la interfaz `IRowset`. Para agregar el `IRowsetLocate` de la interfaz, heredar `CMyProviderRowset` de [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md).  
  
 Agregar la `IRowsetLocate` interfaz es un poco diferente de la mayoría de las interfaces. Para alinear las vtable hacia arriba, OLE DB plantillas del proveedor tienen un parámetro de plantilla para controlar la interfaz derivada. El código siguiente muestra la nueva lista de herencia:  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
// CMyProviderRowset  
class CMyProviderRowset : public CRowsetImpl< CMyProviderRowset,   
      CTextData, CMyProviderCommand, CAtlArray<CTextData>,   
      CSimpleRow,   
          IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate> >  
```  
  
 El cuarto, quinto y sexto parámetros se agregan todos ellos. Este ejemplo utiliza los valores predeterminados para el cuarto y quinto parámetros pero especifican `IRowsetLocateImpl` como el sexto parámetro. `IRowsetLocateImpl`es una clase de plantilla OLE DB que toma dos parámetros de plantilla: estos enlazan la `IRowsetLocate` de la interfaz para la `CMyProviderRowset` clase. Para agregar la mayoría de las interfaces, puede omitir este paso y mover al siguiente. Solo el `IRowsetLocate` y `IRowsetScroll` interfaces deben tratarse de esta manera.  
  
 A continuación, debe indicar el `CMyProviderRowset` para llamar a `QueryInterface` para el `IRowsetLocate` interfaz. Agregue la línea `COM_INTERFACE_ENTRY(IRowsetLocate)` al mapa. El mapa de interfaz para `CMyProviderRowset` debería aparecer como se muestra en el código siguiente:  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
typedef CRowsetImpl< CMyProviderRowset, CTextData, CMyProviderCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate> > _RowsetBaseClass;  
  
BEGIN_COM_MAP(CMyProviderRowset)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 También debe enlazar el mapa en la `CRowsetImpl` clase. Agregue la macro COM_INTERFACE_ENTRY_CHAIN para enlazar en el `CRowsetImpl` mapa. Además, debe crear una definición de tipo denominada `RowsetBaseClass` que contiene la información de herencia. Esta definición de tipo es arbitraria y puede omitirse.  
  
 Por último, controle la **IColumnsInfo:: GetColumnsInfo** llamar. Las macros PROVIDER_COLUMN_ENTRY se utilizaría normalmente para hacer esto. Sin embargo, un consumidor desee utilizar marcadores. Debe poder cambiar las columnas que devuelve el proveedor dependiendo de si el consumidor solicita un marcador.  
  
 Para controlar la **IColumnsInfo:: GetColumnsInfo** llamar, elimine la **PROVIDER_COLUMN** asignar en la `CTextData` clase. La macro PROVIDER_COLUMN_MAP define una función `GetColumnInfo`. Se necesita definir su propio `GetColumnInfo` función. La declaración de función debe tener este aspecto:  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CTextData  
{  
   ...  
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderRowset* pThis,   
        ULONG* pcCols);  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderCommand* pThis,   
        ULONG* pcCols);  
...  
};  
```  
  
 A continuación, implementar la `GetColumnInfo` función en el archivo MyProviderRS.cpp, como se indica a continuación:  
  
```  
////////////////////////////////////////////////////////////////////  
// MyProviderRS.cpp  
  
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
  
ATLCOLUMNINFO* CTextData::GetColumnInfo(CMyProviderCommand* pThis,   
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
  
 `GetColumnInfo`comprueba primero si una propiedad llamada **DBPROP_IRowsetLocate** se establece. OLE DB tiene propiedades para cada una de las interfaces opcionales del objeto de conjunto de filas. Si el consumidor desea utilizar una de estas interfaces opcionales, Establece una propiedad en true. El proveedor, a continuación, puede comprobar esta propiedad y tomar ninguna medida especial basado en ella.  
  
 En su implementación, obtenga la propiedad mediante el puntero al objeto de comando. El `pThis` puntero representa la clase de conjunto de filas o un comando. Puesto que se utilizan plantillas, tiene que pasarlo como un `void` puntero o el código no se compila.  
  
 Especifique una matriz estática para que contenga la información de columna. Si el consumidor no desea que la columna de marcador, se desperdicia una entrada en la matriz. Puede asignar dinámicamente esta matriz, pero debe asegurarse de destruirla correctamente. Este ejemplo define y utiliza las macros ADD_COLUMN_ENTRY y ADD_COLUMN_ENTRY_EX para insertar la información en la matriz. Puede agregar las macros al archivo MyProviderRS.H tal como se muestra en el código siguiente:  
  
```  
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
  
 Para probar el código en el consumidor, debe realizar algunos cambios a la `OnRun` controlador. El primer cambio a la función es agregar código para agregar una propiedad al conjunto de propiedades. El código establece la **DBPROP_IRowsetLocate** propiedad en true, lo que indica al proveedor que desea que la columna de marcador. La `OnRun` código del controlador debería aparecer como sigue:  
  
```  
//////////////////////////////////////////////////////////////////////  
// TestProv Consumer Application in TestProvDlg.cpp  
  
void CTestProvDlg::OnRun()   
{  
   CCommand<CAccessor<CProvider> > table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL, NULL, NULL,   
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
  
 Mientras el bucle contiene código para llamar a la `Compare` método en el `IRowsetLocate` interfaz. El código que se debe pasar siempre porque se van a comparar los mismos marcadores. Además, almacene un marcador en una variable temporal para que se puede utilizar después el tiempo bucle finaliza para llamar a la `MoveToBookmark` función en las plantillas de consumidor. El `MoveToBookmark` llamadas a funciones el `GetRowsAt` método `IRowsetLocate`.  
  
 También debe actualizar el registro de usuario en el consumidor. Agregue una entrada en la clase para controlar un marcador y una entrada en el **COLUMN_MAP**:  
  
```  
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
  
 Cuando haya actualizado el código, debe ser capaz de generar y ejecutar el proveedor con el `IRowsetLocate` interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)