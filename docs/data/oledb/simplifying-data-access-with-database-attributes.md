---
title: "Simplificar el acceso a datos con atributos de base de datos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-attr.db_param"
  - "vc-attr.db_column"
  - "vc-attr.db_accessor"
  - "vc-attr.db_command"
  - "vc-attr.db_table"
  - "vc-attr.db_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atributos [C++], acceso a datos"
  - "atributos [C++], base de datos"
  - "atributos [C++], consumidor OLE DB"
  - "datos [C++], simplificar el acceso"
  - "acceso a datos [C++], atributos de bases de datos"
  - "atributos de bases de datos [C++]"
  - "bases de datos [C++], atributos"
  - "consumidores OLE DB [C++], atributos de bases de datos"
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Simplificar el acceso a datos con atributos de base de datos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra el uso de los atributos de base de datos para simplificar las operaciones con bases de datos.  
  
 La forma más fácil de tener acceso a la información de una base de datos es crear una clase de comando \(o tabla\) y una clase de registro de usuario para una tabla particular de la base de datos.  Los atributos de base de datos simplifican algunas de las declaraciones de plantilla que anteriormente era obligado hacer.  
  
 Para mostrar el uso de los atributos de base de datos, las siguientes secciones presentan dos declaraciones equivalentes de clases de tabla y registro de usuario: la primera utiliza atributos y la segunda plantillas de consumidor OLE DB.  Este código de declaración suele colocarse en un archivo de encabezado cuyo nombre sigue el del objeto de tabla o comando, como por ejemplo Authors.h.  
  
 Al comparar los dos archivos es posible ver lo fácil que es utilizar atributos.  Entre las diferencias se encuentran:  
  
-   Al utilizar atributos sólo hay que declarar una clase: `CAuthors`, mientras que con las plantillas hay que declarar dos: `CAuthorsNoAttrAccessor` y `CAuthorsNoAttr`.  
  
-   La llamada a `db_source` de la versión con atributos equivale a la llamada a `OpenDataSource()` de la declaración de plantilla.  
  
-   La llamada a **db\_table** de la versión con atributos equivale a la siguiente declaración de plantilla:  
  
    ```  
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor> >  
    ```  
  
-   Las llamadas a **db\_column** de la versión con atributos equivalen al mapa de columnas \(ver `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`\) de la declaración de plantilla.  
  
 Los atributos insertan una declaración de clase de registro de usuario.  La clase de registro de usuario equivale a `CAuthorsNoAttrAccessor` en la declaración de plantilla.  Si la clase de tabla es `CAuthors`, la clase de registro de usuario insertado recibe el nombre `CAuthorsAccessor` y sólo se puede ver su declaración en el código insertado.  Para obtener más información, vea "Clases de registro de usuario con atributos", en [Registros de usuario](../../data/oledb/user-records.md).  
  
 Observe que tanto en el código con atributos como en el código de plantilla se deben establecer las propiedades del conjunto de filas utilizando `CDBPropSet::AddProperty`.  
  
 Para obtener más información acerca de los atributos tratados en este tema, vea [Atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
## Declaración de tablas y descriptores de acceso mediante atributos  
 El siguiente código llama a `db_source` y **db\_table** en la clase de tabla.  `db_source` especifica el origen de datos y la conexión que se va a usar.  **db\_table** inserta el código de plantilla apropiado para declarar una clase de tabla.  **db\_column** especifica el mapa de columnas e inserta la declaración del descriptor de acceso.  Se pueden utilizar los atributos de consumidor OLE DB en cualquier proyecto que admita ATL.  
  
 A continuación se muestra la declaración de tabla y del descriptor de acceso con atributos.  
  
```  
//////////////////////////////////////////////////////////////////////  
// Table and accessor declaration using attributes  
// authors.h  
//////////////////////////////////////////////////////////////////////  
  
// Table class declaration  
// (Note that you must provide your own connection string for db_source.)  
[  
   db_source(L"your connection string"),  
   db_table("Authors")  
]  
class CAuthors  
{  
public:  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
   }  
};  
```  
  
## Declaración de tablas y descriptores de acceso mediante plantillas  
 Esta es la declaración de tabla y descriptor de acceso utilizando plantillas.  
  
```  
//////////////////////////////////////////////////////////////////////  
// Table and user record class declaration using templates  
// authors.h  
//////////////////////////////////////////////////////////////////////  
  
// User record class declaration  
class CAuthorsNoAttrAccessor  
{  
public:  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
   LONG m_AuID;  
   TCHAR m_Author[51];  
   SHORT m_YearBorn;  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
   }  
   HRESULT OpenDataSource()  
   {  
      CDataSource _db;  
      HRESULT hr;  
      hr = _db.OpenFromInitializationString(L"your connection string");  
      if (FAILED(hr))  
      {  
#ifdef _DEBUG  
         AtlTraceErrorRecords(hr);  
#endif  
         return hr;  
      }  
      return m_session.Open(_db);  
   }  
   void CloseDataSource()  
   {  
      m_session.Close();  
   }  
   operator const CSession&()  
   {  
      return m_session;  
   }  
   CSession m_session;  
   BEGIN_COLUMN_MAP(CAuthorsNoAttrAccessor)  
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, m_dwAuIDLength, m_dwAuIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, m_dwAuthorLength, m_dwAuthorStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, m_dwYearBornLength, m_dwYearBornStatus)  
   END_COLUMN_MAP()  
};  
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor> >  
{  
public:  
   HRESULT OpenAll()  
   {  
      HRESULT hr;  
      hr = OpenDataSource();  
      if (FAILED(hr))  
         return hr;  
      __if_exists(GetRowsetProperties)  
      {  
         CDBPropSet propset(DBPROPSET_ROWSET);  
         __if_exists(HasBookmark)  
         {  
            propset.AddProperty(DBPROP_IRowsetLocate, true);  
         }  
         GetRowsetProperties(&propset);  
         return OpenRowset(&propset);  
      }  
      __if_not_exists(GetRowsetProperties)  
      {  
         __if_exists(HasBookmark)  
         {  
            CDBPropSet propset(DBPROPSET_ROWSET);  
            propset.AddProperty(DBPROP_IRowsetLocate, true);  
            return OpenRowset(&propset);  
         }  
      }  
      return OpenRowset();  
   }  
   HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)  
   {  
      HRESULT hr = Open(m_session, "Authors", pPropSet);  
#ifdef _DEBUG  
      if(FAILED(hr))  
         AtlTraceErrorRecords(hr);  
#endif  
      return hr;  
   }  
   void CloseAll()  
   {  
      Close();  
      CloseDataSource();  
   }  
};  
```  
  
## Vea también  
 [OLE DB Consumer Attributes](../../windows/ole-db-consumer-attributes.md)   
 [Attributes Walkthroughs](http://msdn.microsoft.com/es-es/73df1d5d-261a-4521-98fb-06dcbf5ec0d0)