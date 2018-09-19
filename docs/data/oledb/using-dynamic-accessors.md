---
title: Utilizar descriptores de acceso dinámicos | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fed93404a6c11addb8068d6140fda48d1c02a253
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056745"
---
# <a name="using-dynamic-accessors"></a>Utilizar descriptores de acceso dinámicos

Descriptores de acceso dinámicos permiten tener acceso a un origen de datos cuando no tiene conocimiento del esquema de base de datos (estructura subyacente). La biblioteca de plantillas OLE DB proporciona varias clases para ayudarle a hacerlo.

El [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) ejemplo muestra cómo usar las clases de descriptor de acceso dinámico para obtener información de columna y crear dinámicamente los descriptores de acceso.

## <a name="using-cdynamicaccessor"></a>Utilizar CDynamicAccessor

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) permite obtener acceso a un origen de datos cuando no tiene conocimiento del esquema de base de datos (estructura subyacente de la base de datos). `CDynamicAccessor` métodos obtienen información de columna como nombres de columna, número y tipo de datos. Utilice esta información de columna para crear un descriptor de acceso de forma dinámica en tiempo de ejecución. La información de columna se almacena en un búfer que se crea y administrado por esta clase. Obtener datos desde el búfer mediante el [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) método.

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```cpp
// Using_Dynamic_Accessors.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );

    CDataSource ds;
    CSession ss;

    CTable<CDynamicAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            DBTYPE type;
            rs.GetColumnType(i, &type );
            printf_s( "Column %d [%S] is of type %d\n",
                      i, rs.GetColumnName(i ), type );

            switch(type )
            {
                case DBTYPE_WSTR:
                    printf_s( "value is %S\n",
                              (WCHAR*)rs.GetValue(i ) );
                break;
                case DBTYPE_STR:
                    printf_s( "value is %s\n",
                              (CHAR*)rs.GetValue(i ) );
                default:
                    printf_s( "value is %d\n",
                              *(long*)rs.GetValue(i ) );
            }
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

    return 0;
}
```

## <a name="using-cdynamicstringaccessor"></a>Utilizar CDynamicStringAccessor

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) funciona como [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), excepto en un aspecto importante. Mientras `CDynamicAccessor` solicita datos en el formato nativo notificado por el proveedor, `CDynamicStringAccessor` solicita que el proveedor recupere todos los datos que se obtiene acceso desde el almacén de datos como datos de cadena. Esto es especialmente útil para tareas sencillas que no requieren el cálculo de valores en el almacén de datos, como mostrar o imprimir el contenido del almacén de datos.

Use `CDynamicStringAccessor` métodos para obtener información de columna. Utilice esta información de columna para crear un descriptor de acceso de forma dinámica en tiempo de ejecución. La información de columna se almacena en un búfer creado y administrado por esta clase. Obtener datos desde el búfer mediante [CDynamicStringAccessor:: GetString](../../data/oledb/cdynamicstringaccessor-getstring.md) o almacenarlos en el búfer mediante [CDynamicStringAccessor:: SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```cpp
// Using_Dynamic_Accessors_b.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );
    if (hr != S_OK)
    {
        exit (-1);
    }

    CDataSource ds;
    CSession ss;

    CTable<CDynamicStringAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            printf_s( "column %d value is %s\n",
                      i, rs.GetString(i ) );
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

   return 0;
}
```

## <a name="using-cdynamicparameteraccessor"></a>Using CDynamicParameterAccessor

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) es similar a [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), salvo que `CDynamicParameterAccessor` Obtiene la información de parámetro que se puede establecer mediante una llamada a la [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) interfaz. El proveedor debe admitir `ICommandWithParameters` para que el consumidor pueda usar esta clase.

La información de parámetros se almacena en un búfer creado y administrado por esta clase. Obtener datos de parámetro desde el búfer mediante [CDynamicParameterAccessor:: GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) y [CDynamicParameterAccessor:: GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Para obtener un ejemplo que muestra cómo utilizar esta clase para ejecutar un procedimiento almacenado de SQL Server y obtener los valores de parámetro de salida, vea el [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) código de ejemplo en el [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) repositorio de GitHub.

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor (Clase)](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[Ejemplo DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)  