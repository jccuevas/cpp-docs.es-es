---
title: Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: 25bb370c0714bfef97bc6659deae2fbd21aed23f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664573"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente

Cuando se usa el **el Asistente para consumidores OLE DB ATL** para crear un consumidor, el asistente genera un miembro de datos en la clase de registro de usuario para cada campo que especifique en el mapa de columnas. Cada miembro de datos es de tipo `DWORD` y contiene un valor de estado correspondiente a su campo correspondiente.

Por ejemplo, para un miembro de datos *m_OwnerID*, el asistente genera un miembro de datos adicionales para el estado de campo (*dwOwnerIDStatus*) y otro para la longitud de campo (*dwOwnerIDLength*). También genera un mapa de columnas con entradas COLUMN_ENTRY_LENGTH_STATUS.

Esto se muestra en el código siguiente:

```cpp
class CAuthorsAccessor
{
public:
   LONG m_AuID;
   TCHAR m_Author[53];
   LONG m_YearBorn;

   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;

   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;

    DEFINE_COMMAND_EX(CAuthorsAccessor, L" \
    SELECT \
        AuID, \
        Author, \
        YearBorn \
        FROM dbo.Authors")

    BEGIN_COLUMN_MAP(CAuthorsAccessor)
       COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)
       COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)
    END_COLUMN_MAP()
...
```

> [!NOTE]
> Si modifica la clase de registro de usuario o escribe su propio consumidor, las variables de datos deben preceder a las variables de estado y longitud.

Puede usar los valores de estado con fines de depuración. Si el código generado por el **el Asistente para consumidores OLE DB ATL** genera errores de compilación como DB_S_ERRORSOCCURRED o DB_E_ERRORSOCCURRED, primero debe buscar en los valores actuales de los miembros de datos de estado de campo. Aquellos usuarios que tienen valores distintos de cero corresponden a las columnas incorrectos.

También puede usar los valores de estado para establecer un valor NULL para un campo determinado. Esto ayuda a en los casos en los que desee distinguir un valor de campo como NULL en lugar de cero. Depende de usted decidir si NULL es un valor válido o un valor especial y decidir cómo debe controlar su aplicación. OLE DB define DBSTATUS_S_ISNULL como la forma correcta de especificar un valor NULL genérico. Si el consumidor lee los datos y el valor es null, el campo de estado se establece en DBSTATUS_S_ISNULL. Si el consumidor desea establecer un valor NULL, el consumidor establece el valor de estado en DBSTATUS_S_ISNULL antes de llamar al proveedor.

A continuación, abra Oledb.h y busque DBSTATUSENUM. A continuación, puede hacer coincidir el valor numérico del estado distinto de cero con los valores de enumeración DBSTATUSENUM. Si el nombre de la enumeración no es suficiente para saber cuál es el problema, consulte el **estado** tema en el **valores de enlace de datos** sección de la [Guía del programador de OLE DB](/previous-versions/windows/desktop/ms713643). Este tema contiene las tablas de valores de estado que se utiliza al obtener o establecer los datos. Para obtener información acerca de los valores de longitud, vea el **longitud** tema en la misma sección.

## <a name="retrieving-the-length-or-status-of-a-column"></a>Recuperar la longitud o el estado de una columna

Puede recuperar la longitud de una columna de longitud variable o el estado de una columna (para buscar DBSTATUS_S_ISNULL, por ejemplo):

- Para obtener la longitud, use la macro COLUMN_ENTRY_LENGTH.

- Para obtener el estado, use la macro COLUMN_ENTRY_STATUS.

- Para obtener ambos, use COLUMN_ENTRY_LENGTH_STATUS, como se muestra:

    ```cpp
    class CProducts
    {
    public:
       char      szName[40];
       long      nNameLength;
       DBSTATUS   nNameStatus;

    BEGIN_COLUMN_MAP(CProducts)
    // Bind the column to CProducts.m_ProductName.
    // nOrdinal is zero-based, so the column number of m_ProductName is 1.
       COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)
    END_COLUMN_MAP()
    };
    ```

- A continuación, tener acceso a la longitud o el estado tal como se muestra:

    ```cpp
    CTable<CAccessor<CProducts >> product;
    CSession session;

    product.Open(session, "Product");

    while (product.MoveNext() == S_OK)
    {
       // Check the product name isn't NULL before tracing it
       if (product.nNameStatus == DBSTATUS_S_OK)
          ATLTRACE("%s is %d characters\n", product.szName, product.nNameLength);
    }
    ```

Cuando usas `CDynamicAccessor`, la longitud y el estado se enlazan automáticamente. Para recuperar los valores de longitud y el estado, use la `GetLength` y `GetStatus` funciones miembro.

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)