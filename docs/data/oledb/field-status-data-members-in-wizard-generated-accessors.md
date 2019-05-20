---
title: Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: a6623cb02f14650d92e4adabed749b0b37725d45
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707560"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente

::: moniker range="vs-2019"

El Asistente para consumidores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores. Puede seguir agregando la funcionalidad manualmente. Para obtener más información, consulte [Crear un consumidor sin utilizar un asistente](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Cuando se usa el **Asistente para consumidores OLE DB ATL** para crear un consumidor, genera un miembro de datos en la clase de registro de usuario para cada campo que especifique en la asignación de columnas. Cada miembro de datos es de tipo `DWORD` y contiene un valor de estado correspondiente a su campo correspondiente.

Por ejemplo, para un miembro de datos *m_OwnerID*, el asistente genera un miembro de datos adicional para el estado de campo (*dwOwnerIDStatus*) y otro para la longitud de campo (*dwOwnerIDLength*). También genera una asignación de columnas con entradas COLUMN_ENTRY_LENGTH_STATUS.

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

Puede usar los valores de estado con fines de depuración. Si el código generado por el **Asistente para consumidores OLE DB ATL** genera errores de compilación como DB_S_ERRORSOCCURRED o DB_E_ERRORSOCCURRED, primero debe buscar en los valores actuales de los miembros de datos de estado de campo. Aquellos usuarios que tienen valores distintos de cero corresponden a las columnas incorrectas.

También puede usar los valores de estado para establecer un valor NULL para un campo determinado. Esto ayuda en los casos en los que desee distinguir un valor de campo como NULL en lugar de cero. Tendrá que decidir si NULL es un valor válido o un valor especial, y determinar cómo debe controlar su aplicación. OLE DB define DBSTATUS_S_ISNULL como la forma correcta de especificar un valor NULL genérico. Si el consumidor lee los datos y el valor es NULL, el campo de estado se establece en DBSTATUS_S_ISNULL. Si el consumidor desea establecer un valor NULL, este establece el valor de estado en DBSTATUS_S_ISNULL antes de llamar al proveedor.

A continuación, abra Oledb.h y busque DBSTATUSENUM. Después, puede hacer coincidir el valor numérico del estado distinto de cero con los valores de enumeración DBSTATUSENUM. Si el nombre de la enumeración no es suficiente para saber cuál es el problema, consulte el tema de **estado** en la sección de **valores de enlace de datos** de la [Guía del programador de OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Este tema contiene las tablas de valores de estado que se utilizan al obtener o establecer los datos. Para obtener información sobre los valores de longitud, vea el tema sobre **longitud** en la misma sección.

## <a name="retrieving-the-length-or-status-of-a-column"></a>Recuperación de la longitud o el estado de una columna

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

- A continuación, acceda a la longitud o al estado tal como se muestra:

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

Cuando usa `CDynamicAccessor`, la longitud y el estado se enlazan automáticamente. Para recuperar los valores de longitud y el estado, use la `GetLength` y `GetStatus` funciones miembro.

::: moniker-end

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)