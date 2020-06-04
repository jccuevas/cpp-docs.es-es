---
title: Simplificar el acceso a datos con atributos de base de datos
ms.date: 10/19/2018
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
ms.openlocfilehash: d22f8a25bc7bb58f72346a15edb51f062c44e1b4
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79546180"
---
# <a name="simplifying-data-access-with-database-attributes"></a>Simplificar el acceso a datos con atributos de base de datos

En este tema se muestra el uso de atributos de base de datos para simplificar las operaciones de base de datos.

La manera básica de obtener acceso a la información de una base de datos consiste en crear una clase de comando (o tabla) y una clase de registro de usuario para una tabla determinada de la base de datos. Los atributos de base de datos simplifican algunas de las declaraciones de plantilla que tenía anteriormente.

Para demostrar el uso de los atributos de base de datos, en las secciones siguientes se muestran dos declaraciones de clase de registro de usuario y tabla equivalentes: la primera usa los atributos y la segunda utiliza OLE DB plantillas. Este código de declaración suele colocarse en un archivo de encabezado denominado para la tabla o el objeto de comando, por ejemplo, authors. h.

Al comparar los dos archivos, puede ver la cantidad más sencilla de usar atributos. Entre las diferencias se encuentran:

- Mediante el uso de atributos, solo tiene que declarar una clase: `CAuthors`, mientras que con las plantillas tiene que declarar dos: `CAuthorsNoAttrAccessor` y `CAuthorsNoAttr`.

- La llamada a `db_source` en la versión con atributos es equivalente a la llamada `OpenDataSource()` en la declaración de la plantilla.

- La llamada a `db_table` en la versión con atributos es equivalente a la siguiente declaración de plantilla:

    ```cpp
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
    ```

- Las llamadas `db_column` en la versión con atributos son equivalentes al mapa de columnas (vea `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) en la declaración de plantilla.

Los atributos insertan una declaración de clase de registro de usuario. La clase de registro de usuario es igual a `CAuthorsNoAttrAccessor` en la declaración de plantilla. Si la clase de tabla es `CAuthors`, la clase de registro de usuario insertada se denomina `CAuthorsAccessor`y solo puede ver su declaración en el código insertado. Para obtener más información, vea "clases de registro de usuario insertadas por atributos" en [registros de usuario](../../data/oledb/user-records.md).

En el código con atributos y con plantilla, debe establecer las propiedades del conjunto de filas mediante `CDBPropSet::AddProperty`.

Para obtener información sobre los atributos descritos en este tema, vea [OLE DB atributos del consumidor](../../windows/ole-db-consumer-attributes.md).

> [!NOTE]
> Se requieren las siguientes instrucciones `include` para compilar los ejemplos siguientes:

> ```cpp
> #include <atlbase.h>
> #include <atlplus.h>
> #include <atldbcli.h>
> ```

## <a name="table-and-accessor-declaration-using-attributes"></a>Declaración de tabla y descriptor de acceso con atributos

En el código siguiente se llama a `db_source` y `db_table` en la clase Table. `db_source` especifica el origen de datos y la conexión que se va a utilizar. `db_table` inserta el código de plantilla adecuado para declarar una clase de tabla. `db_column` especifique el mapa de columnas e inserte la declaración del descriptor de acceso. Puede utilizar OLE DB atributos de consumidor en cualquier proyecto que admita ATL.

A continuación se muestra la declaración de tabla y descriptor de acceso con atributos:

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

## <a name="table-and-accessor-declaration-using-templates"></a>Declaración de tabla y descriptor de acceso mediante plantillas

Esta es la declaración de tabla y descriptor de acceso mediante plantillas.

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

## <a name="see-also"></a>Consulte también

[Atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md)
