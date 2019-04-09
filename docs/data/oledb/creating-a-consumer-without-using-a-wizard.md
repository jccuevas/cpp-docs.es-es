---
title: Crear un consumidor sin utilizar un asistente
ms.date: 10/12/2018
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 029fe6866df81d366cc3bc15096f638791faa413
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030425"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Crear un consumidor sin utilizar un asistente

En el siguiente ejemplo se da por supuesto que va a agregar compatibilidad de consumidor OLE DB a un proyecto ATL existente. Si desea agregar compatibilidad de consumidor OLE DB a una aplicación MFC, debe ejecutar el **MFC Application Wizard**, que crea todo el soporte necesario e invoca las rutinas MFC necesarias para ejecutar la aplicación.

Para agregar compatibilidad de consumidor OLE DB sin usar el **el Asistente para consumidores OLE DB ATL**:

- En el archivo pch.h, agregue lo siguiente `#include` instrucciones:

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

Mediante programación, un consumidor normalmente realiza la siguiente secuencia de operaciones:

1. Cree una clase de registro de usuario que enlaza las columnas a las variables locales. En este ejemplo, `CMyTableNameAccessor` es la clase de registro de usuario (consulte [registros de usuario](../../data/oledb/user-records.md)). Esta clase contiene el mapa de columnas y la asignación de parámetro. Declarar a un miembro de datos en la clase de registro de usuario para cada campo que especifique en el mapa de columnas; para cada uno de estos miembros de datos, también declarar un miembro de datos de estado y un miembro de datos de longitud. Para obtener más información, consulte [miembros de datos de estado de campo en los descriptores de acceso](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

    > [!NOTE]
    > Si escribe su propio consumidor, las variables de datos deben preceder a las variables de estado y longitud.

- Crear una instancia de un origen de datos y una sesión. Decidir qué tipo de descriptor de acceso y el conjunto de filas a usar y, a continuación, crear una instancia de un conjunto de filas utilizando [CCommand](../../data/oledb/ccommand-class.md) o [CTable](../../data/oledb/ctable-class.md):

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- Llamar a `CoInitialize` inicializar COM. Esto se denomina en el código principal. Por ejemplo:

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- Llame a [CDataSource:: Open](../../data/oledb/cdatasource-open.md) o uno de sus variaciones.

- Abra una conexión al origen de datos, abra la sesión y abra e inicializar el conjunto de filas (y si un comando, también ejecutar):

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- Si lo desea, conjunto de filas propiedades mediante `CDBPropSet::AddProperty` y pasarlos como parámetro a `rs.Open`. Para obtener un ejemplo de cómo hacerlo, consulte `GetRowsetProperties` en [generadas métodos](../../data/oledb/consumer-wizard-generated-methods.md).

- Ahora puede usar el conjunto de filas para recuperar o manipular los datos.

- Cuando se realiza la aplicación, cierre la conexión, la sesión y el conjunto de filas:

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   Si usa un comando, puede llamar a `ReleaseCommand` después `Close`. El código de ejemplo [CCommand:: Close](../../data/oledb/ccommand-close.md) muestra cómo llamar a `Close` y `ReleaseCommand`.

- Llame a `CoUnInitialize` para anular la inicialización de COM. Esto se denomina en el código principal.

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>Vea también

[Crear un consumidor OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)