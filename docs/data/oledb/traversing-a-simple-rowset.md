---
title: Recorrer un conjunto de filas simple
ms.date: 10/19/2018
helpviewer_keywords:
- data access [C++], rowsets
- rowsets [C++], accessing
- simple rowsets
- OLE DB consumers [C++], database attributes
- accessors [C++], rowsets
ms.assetid: b45acf16-4029-429d-ab8d-b7fba98b9740
ms.openlocfilehash: a6b2ebf918f42e274c372d1dda1e277f7fd49cd5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209474"
---
# <a name="traversing-a-simple-rowset"></a>Recorrer un conjunto de filas simple

En el ejemplo siguiente se muestra el acceso rápido y sencillo a bases de datos que no implica comandos. El siguiente código de consumidor, en un proyecto ATL, recupera registros de una tabla denominada *artistas* en una base de datos de Microsoft Access mediante el proveedor de OLE DB de Microsoft para ODBC. El código crea un objeto de tabla [CTable](../../data/oledb/ctable-class.md) con un descriptor de acceso basado en la clase de registro de usuario `CArtists`. Se abre una conexión, se abre una sesión en la conexión y se abre la tabla en la sesión.

```cpp
#include <atldbcli.h>
#include <iostream>

using namespace std;

int main()
{
    CDataSource connection;
    CSession session;
    CTable<CAccessor<CArtists>> artists;

    LPCSTR clsid; // Initialize CLSID_MSDASQL here
    LPCTSTR pName = L"NWind";

    // Open the connection, session, and table, specifying authentication
    // using Windows NT integrated security. Hard-coding a password is a major
    // security weakness.
    connection.Open(clsid, pName, NULL, NULL, DBPROP_AUTH_INTEGRATED);

    session.Open(connection);

    artists.Open(session, "Artists");

    // Get data from the rowset
    while (artists.MoveNext() == S_OK)
    {
       cout << artists.m_szFirstName;
       cout << artists.m_szLastName;
    }

    return 0;
}
```

El registro de usuario, `CArtists`, es similar al de este ejemplo:

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()
};
```

## <a name="see-also"></a>Consulte también

[Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
