---
title: Simplificar el acceso a datos con atributos de base de datos | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- data [C++], simplifying access
- data access [C++], database attributes
- database attributes [C++]
- OLE DB consumers [C++], database attributes
- attributes [C++], OLE DB consumer
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2689aab8b33c01c9a4d72b231a11a251813ac625
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808022"
---
# <a name="simplifying-data-access-with-database-attributes"></a>Simplificar el acceso a datos con atributos de base de datos

En este tema se muestra el uso de atributos de la base de datos para simplificar las operaciones de base de datos.  
  
Es la forma básica para tener acceso a información desde una base de datos crear una clase de comando (o tabla) y una clase de registro de usuario para una tabla determinada en la base de datos. Los atributos de base de datos simplifican algunas de las declaraciones de plantilla que previamente tenía que hacer.  
  
Para demostrar el uso de atributos de la base de datos, las secciones siguientes muestran dos tabla equivalente y las declaraciones de clase de registro de usuario: el primero usa los atributos y la segunda usa plantillas OLE DB. Este código de declaración se suele colocar en un archivo de encabezado denominado para el objeto de tabla o un comando, por ejemplo, Authors.h.  
  
Comparando los dos archivos, puede ver cómo mucho más sencillo es utilizar los atributos. Entre las diferencias son:  
  
- Uso de atributos, solo tiene que declarar una clase: `CAuthors`, mientras que con las plantillas de tener que declarar dos: `CAuthorsNoAttrAccessor` y `CAuthorsNoAttr`.  
  
- El `db_source` llamada en la versión con atributos es equivalente a la `OpenDataSource()` llamar a en la declaración de plantilla.  
  
- El `db_table` llamada en la versión con atributos es equivalente a la siguiente declaración de plantilla:  
  
    ```cpp  
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>  
    ```  
  
- El `db_column` llamadas de la versión con atributos son equivalentes a la asignación de columna (consulte `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) en la declaración de plantilla.  
  
Los atributos insertan una declaración de clase de registro de usuario para usted. La clase de registro de usuario es igual a `CAuthorsNoAttrAccessor` en la declaración de plantilla. Si la clase de tabla es `CAuthors`, la clase de registro de usuario insertado se denomina `CAuthorsAccessor`, y solo se puede ver su declaración en el código insertado. Para obtener más información, vea "Clases de registro de usuario con atributos" en [registros de usuario](../../data/oledb/user-records.md).  
  
En los atributos y el código de plantilla, debe establecer las propiedades del conjunto de filas mediante `CDBPropSet::AddProperty`.  
  
Para obtener información acerca de los atributos tratados en este tema, consulte [atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md).

> [!NOTE]
> La siguiente `include` instrucciones son necesarias para compilar los ejemplos siguientes:
> ```cpp
> #include <atlbase.h>  
> #include <atlplus.h>  
> #include <atldbcli.h>    
> ```

## <a name="table-and-accessor-declaration-using-attributes"></a>Tabla y la declaración del descriptor de acceso mediante atributos  

El código siguiente llama `db_source` y `db_table` en la clase de tabla. `db_source` Especifica el origen de datos y la conexión que se usará. `db_table` Inserta el código de plantilla apropiado para declarar una clase de tabla. `db_column` Especifica el mapa de columnas e insertar la declaración del descriptor de acceso. Puede usar atributos de consumidor OLE DB en cualquier proyecto que admita ATL.  
  
Aquí es la declaración de tabla y el descriptor de acceso mediante atributos:  
  
```cpp
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
   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;
   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;
   [db_column("1", status = "m_dwAuIDStatus", length = "m_dwAuIDLength")] LONG m_AuID;
   [db_column("2", status = "m_dwAuthorStatus", length = "m_dwAuthorLength")] TCHAR m_Author[51];
   [db_column("3", status = "m_dwYearBornStatus", length = "m_dwYearBornLength")] SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
   }  
};  
```  
  
## <a name="table-and-accessor-declaration-using-templates"></a>Tabla y la declaración del descriptor de acceso mediante plantillas  

Aquí es la declaración de tabla y el descriptor de acceso mediante plantillas.  
  
```cpp
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
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>  
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
  
## <a name="see-also"></a>Vea también  

[Atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md)   
