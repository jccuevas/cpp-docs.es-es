---
title: "Compatibilidad del proveedor con los marcadores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marcadores, OLE DB"
  - "IRowsetLocate (clase)"
  - "IRowsetLocate (clase), compatibilidad del proveedor con los marcadores"
  - "plantillas del proveedor OLE DB, marcadores"
  - "proveedores OLE DB, compatibilidad con marcadores"
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Compatibilidad del proveedor con los marcadores
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El ejemplo de este tema agrega la interfaz `IRowsetLocate` a la clase `CMyProviderRowset`.  En la mayoría de los casos, empieza por agregar una interfaz a un objeto COM existente.  Después podrá probarlo agregando más llamadas de las plantillas de consumidor.  El ejemplo muestra cómo:  
  
-   Agregar una interfaz a un proveedor.  
  
-   Determinar dinámicamente las columnas que se devuelven al consumidor.  
  
-   Agregar compatibilidad con marcadores.  
  
 La interfaz `IRowsetLocate` hereda de la interfaz `IRowset`.  Para agregar la interfaz `IRowsetLocate`, herede `CMyProviderRowset` de [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md).  
  
 El proceso de agregar la interfaz `IRowsetLocate` es ligeramente diferente del necesario para agregar la mayoría de las interfaces.  Para alinear las VTABLE, las plantillas de proveedor OLE DB tienen un parámetro de plantilla para controlar la interfaz derivada.  El siguiente fragmento de código muestra la nueva lista de herencia:  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
// CMyProviderRowset  
class CMyProviderRowset : public CRowsetImpl< CMyProviderRowset,   
      CTextData, CMyProviderCommand, CAtlArray<CTextData>,   
      CSimpleRow,   
          IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate> >  
```  
  
 Los parámetros cuarto, quinto y sexto se agregan todos.  En este ejemplo se usan los valores predeterminados de los parámetros cuarto y quinto, pero se especifica `IRowsetLocateImpl` como el sexto parámetro.  `IRowsetLocateImpl` es una clase de plantilla OLE DB que toma dos parámetros de plantilla: estos enlazan la interfaz `IRowsetLocate` con la clase `CMyProviderRowset`.  Para agregar la mayoría de las interfaces, puede omitir este paso y pasar al siguiente.  Sólo hay que controlar de esta forma las interfaces `IRowsetLocate` e `IRowsetScroll`.  
  
 Después debe indicar a `CMyProviderRowset` que llame a `QueryInterface` para la interfaz `IRowsetLocate`.  Agregue la línea `COM_INTERFACE_ENTRY(IRowsetLocate)` al mapa.  El mapa de interfaz de `CMyProviderRowset` debe aparecer de la manera indicada en el siguiente código:  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
typedef CRowsetImpl< CMyProviderRowset, CTextData, CMyProviderCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate> > _RowsetBaseClass;  
  
BEGIN_COM_MAP(CMyProviderRowset)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 También tiene que enlazar el mapa a la clase `CRowsetImpl`.  Agregue la macro COM\_INTERFACE\_ENTRY\_CHAIN para enlazar el mapa `CRowsetImpl`.  Además, cree una definición de tipo denominada `RowsetBaseClass` que contenga información de herencia.  Esta definición de tipo es arbitraria y puede pasarse por alto.  
  
 Por último, controle la llamada a **IColumnsInfo::GetColumnsInfo**.  Normalmente se utilizan las macros PROVIDER\_COLUMN\_ENTRY para esto.  Sin embargo, puede que un consumidor desee utilizar marcadores.  Debe poder cambiar las columnas que devuelve el proveedor en función de si el consumidor solicita un marcador.  
  
 Para controlar la llamada **IColumnsInfo::GetColumnsInfo**, elimine el mapa **PROVIDER\_COLUMN** de la clase `CTextData`.  La macro PROVIDER\_COLUMN\_MAP define una función `GetColumnInfo`.  Debe definir su propia función `GetColumnInfo`.  La declaración de función debe ser similar a la siguiente:  
  
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
  
 A continuación, implemente la función `GetColumnInfo` en el archivo MyProviderRS.cpp, de la manera siguiente:  
  
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
  
 `GetColumnInfo` comprueba, en primer lugar, si se establece el valor de la propiedad **DBPROP\_IRowsetLocate**.  OLE DB tiene propiedades para cada una de las interfaces opcionales del objeto de conjunto de filas.  Si el consumidor desea utilizar una de estas interfaces opcionales, establece el valor de una propiedad en true.  El proveedor puede comprobar después el valor de esta propiedad y optar por una acción determinada basándose en ella.  
  
 En la implementación, obtiene el valor de la propiedad mediante el puntero al objeto de comando.  El puntero `pThis` representa la clase de conjunto de filas o comandos.  Puesto que se utilizan plantillas, debe pasarlo como puntero `void`. De lo contrario, no se puede compilar el código.  
  
 Especifique una matriz estática para que contenga la información de columna.  Si el consumidor no desea la columna de marcador, se desperdiciará una entrada de matriz.  Puede asignar dinámicamente esta matriz, pero se debe asegurar de destruirla correctamente.  En este ejemplo se definen y utilizan las macros ADD\_COLUMN\_ENTRY y ADD\_COLUMN\_ENTRY\_EX para insertar la información en la matriz.  Puede agregar las macros al archivo MyProviderRS.H de la manera indicada en las siguientes líneas de código:  
  
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
  
 Para probar el código en el consumidor, tiene que hacer algunos cambios en el controlador `OnRun`.  El primer cambio realizado en la función es que debe agregar código para agregar una propiedad al conjunto de propiedades.  El código establece el valor de la propiedad **DBPROP\_IRowsetLocate** en true y, por tanto, indica al proveedor que desea la columna del marcador.  El código del controlador `OnRun` debe ser parecido al siguiente:  
  
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
  
 El bucle while contiene código para llamar al método `Compare` de la interfaz `IRowsetLocate`.  El código que tiene debe superar siempre la prueba, puesto que se está comparando con los mismos marcadores.  Almacene también un marcador en una variable temporal para poder utilizarla cuando el bucle while deje de llamar a la función `MoveToBookmark` en las plantillas de consumidor.  La función `MoveToBookmark` llama al método `GetRowsAt` de `IRowsetLocate`.  
  
 También debe actualizar el registro de usuario en el consumidor.  Agregue una entrada a la clase para controlar un marcador y una entrada a **COLUMN\_MAP**:  
  
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
  
 Cuando haya actualizado el código, debe poder compilar y ejecutar el proveedor con la interfaz `IRowsetLocate`.  
  
## Vea también  
 [Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)