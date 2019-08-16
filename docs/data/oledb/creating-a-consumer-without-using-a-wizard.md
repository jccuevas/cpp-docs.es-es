---
title: Crear un consumidor sin utilizar un asistente
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 421723ed561e8ed986a64024c4c5d29c9fba6110
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525116"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Crear un consumidor sin utilizar un asistente

En el siguiente ejemplo se da por supuesto que va a agregar compatibilidad del consumidor OLE DB con un proyecto ATL existente. Si desea agregar compatibilidad del consumidor OLE DB con una aplicación MFC, debe ejecutar el **Asistente para aplicaciones MFC**, que crea toda la compatibilidad necesaria e invoca las rutinas MFC necesarias para ejecutar la aplicación.

Agregar compatibilidad del consumidor OLE DB sin usar el **Asistente para consumidores OLE DB ATL**:

- En el archivo pch.h, agregue las siguientes instrucciones `#include`:

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

Mediante programación, un consumidor normalmente realiza la siguiente secuencia de operaciones:

1. Cree una clase de registro de usuario que enlaza las columnas a las variables locales. En este ejemplo, `CMyTableNameAccessor` es la clase de registro de usuario (consulte [Registros de usuario](../../data/oledb/user-records.md)). Esta clase contiene la asignación de columnas y de parámetros. Declare un miembro de datos en la clase de registro de usuario para cada campo que especifique en la asignación de columnas; para cada uno de estos miembros de datos, declare también un miembro de datos de estado y un miembro de datos de longitud. Para obtener más información, consulte [Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

    > [!NOTE]
    > Si escribe su propio consumidor, las variables de datos deben preceder a las variables de estado y longitud.

- Cree una instancia de un origen de datos y una sesión. Decida qué tipo de descriptor de acceso y el conjunto de filas que usar y, a continuación, cree una instancia de un conjunto de filas utilizando [CCommand](../../data/oledb/ccommand-class.md) o [CTable](../../data/oledb/ctable-class.md):

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- Llame a `CoInitialize` para crear una instancia de COM. Esto se realiza en el código principal. Por ejemplo:

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- Llame a [CDataSource::Open](../../data/oledb/cdatasource-open.md) o a una de sus variaciones.

- Abra una conexión al origen de datos, abra la sesión y abra e inicialice el conjunto de filas (y si hay un comando, ejecútelo también):

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- Si lo desea, establezca las propiedades del conjunto de filas mediante `CDBPropSet::AddProperty` y páselas como parámetro a `rs.Open`. Para obtener un ejemplo de cómo hacerlo, consulte `GetRowsetProperties` en [Métodos generados por el Asistente para consumidores](../../data/oledb/consumer-wizard-generated-methods.md).

- Ahora puede usar el conjunto de filas para recuperar o manipular los datos.

- Cuando se realiza la aplicación, cierre la conexión, la sesión y el conjunto de filas:

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   Si usa un comando, puede llamar a `ReleaseCommand` después de `Close`. El código de ejemplo [CCommand::Close](../../data/oledb/ccommand-close.md) muestra cómo llamar a `Close` y `ReleaseCommand`.

- Llame a `CoUnInitialize` para inicializar COM. Esto se realiza en el código principal.

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>Vea también

[Crear un consumidor OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)