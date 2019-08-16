---
title: Admitir conjuntos de filas de esquema
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: 1ad1a91e8a79238eee773d92a756b0238e8901d5
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707495"
---
# <a name="supporting-schema-rowsets"></a>Admitir conjuntos de filas de esquema

Los conjuntos de filas de esquema permiten a los consumidores obtener información de un almacén de datos sin conocer su estructura subyacente o esquema. Por ejemplo, un almacén de datos podría tener tablas organizadas en una jerarquía definida por el usuario, por lo que no habría ninguna manera de garantizar el conocimiento del esquema, excepto si se lee. Otro ejemplo: los asistentes de Visual C++ utilizan conjuntos de filas de esquema con el fin de generar descriptores de acceso para el consumidor. Para permitir que el consumidor haga esta tarea, el objeto de sesión del proveedor expone los métodos en la interfaz [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)). En aplicaciones de Visual C++ aplicaciones, utilizará la clase [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) para implementar `IDBSchemaRowset`.

`IDBSchemaRowsetImpl` admite los siguientes métodos:

- [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) comprueba la validez de las restricciones en un conjunto de filas de esquema.

- [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) implementa una función de creación de objetos COM para el objeto especificado por el parámetro de la plantilla.

- [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) especifica qué restricciones se admiten en un conjunto de filas de esquema determinado.

- [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) devuelve un conjunto de filas de esquema (se hereda de la interfaz).

- [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) devuelve una lista de conjuntos de filas de esquema a los que puede acceder `IDBSchemaRowsetImpl::GetRowset` (se hereda de la interfaz).

## <a name="atl-ole-db-provider-wizard-support"></a>Compatibilidad del Asistente para proveedores OLE DB ATL

::: moniker range="vs-2019"

El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

El **Asistente para proveedores OLE DB ATL** crea tres clases de esquema en el archivo de encabezado de sesión:

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

Estas clases responden a las solicitudes de consumidor de la información de esquema. Tenga en cuenta que la especificación OLE DB requiere que se admitan estos tres conjuntos de filas de esquema:

- **C**<em>ShortName</em>**SessionTRSchemaRowset** controla las solicitudes de información de tabla (el conjunto de filas de esquema DBSCHEMA_TABLES).

- **C**<em>ShortName</em>**SessionColSchemaRowset** controla las solicitudes de información de columna (el conjunto de filas de esquema DBSCHEMA_COLUMNS). El asistente proporciona implementaciones de ejemplo para estas clases, que devuelven información de esquema para un proveedor de denegación de servicio.

- **C**<em>ShortName</em>**SessionPTSchemaRowset** controla las solicitudes de información de esquema sobre el tipo de proveedor (el conjunto de filas de esquema DBSCHEMA_PROVIDER_TYPES). La implementación predeterminada que proporciona el asistente devuelve S_OK.

Puede personalizar estas clases para controlar la información de esquema apropiada para el proveedor:

- En **C**<em>ShortName</em>**SessionTRSchemaRowset**, debe rellenar los campos de catálogo, tabla y descripción (`trData.m_szType`, `trData.m_szTable` y `trData.m_szDesc`). El ejemplo que genera el asistente utiliza una única fila (tabla). Otros proveedores pueden devolver más de una tabla.

- En **C**<em>ShortName</em>**SessionColSchemaRowset**, pase el nombre de la tabla como `DBID`.

::: moniker-end

## <a name="setting-restrictions"></a>Establecimiento de restricciones

Un concepto importante en la compatibilidad de los conjuntos de filas de esquema es el establecimiento de restricciones, que se realiza con `SetRestrictions`. Las restricciones permiten a los clientes obtener solo las filas coincidentes (por ejemplo, buscar todas las columnas de la tabla "MyTable"). Las restricciones son opcionales y, en caso de que no se admita ninguna (comportamiento predeterminado), se devuelven siempre todos los datos. Para obtener un ejemplo de un proveedor que admite conjuntos de filas de esquema, vea el ejemplo [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV).

## <a name="setting-up-the-schema-map"></a>Configuración de la asignación de esquema

Configure una asignación de esquema, como esta en el archivo Session.h de UpdatePV:

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

Para admitir `IDBSchemaRowset`, DBSCHEMA_TABLES, DBSCHEMA_COLUMNS y DBSCHEMA_PROVIDER_TYPES también se deben admitir. Puede agregar más conjuntos de filas de esquema siempre que desee.

Declare una clase de conjunto de filas de esquema con un método `Execute` como `CUpdateSessionTRSchemaRowset` en `UpdatePV`:

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession` se hereda de `IDBSchemaRowsetImpl`, por lo que tiene todos los métodos de control de restricciones. Mediante `CSchemaRowsetImpl`, declare tres clases secundarias (se muestran en la asignación de esquema anterior): `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset` y `CUpdateSessionPTSchemaRowset`. Cada una de estas clases secundarias tiene un método `Execute` que controla su conjunto de restricciones correspondiente (criterios de búsqueda). Cada método `Execute` compara los valores de los parámetros *cRestrictions* y *rgRestrictions*. Vea la descripción de estos parámetros en [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).

Para obtener más información sobre qué restricciones corresponden a un conjunto de filas de esquema determinado, consulte la tabla de GUID de conjuntos de filas de esquema en [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)), en la **referencia del programador de OLE DB** de Windows SDK.

Por ejemplo, si se admite la restricción TABLE_NAME en DBSCHEMA_TABLES, haría lo siguiente:

En primer lugar, busque DBSCHEMA_TABLES y vea si admite cuatro restricciones (en orden).

|Restricción del conjunto de filas de esquema|Valor de restricción|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1 (binario 1)|
|TABLE_SCHEMA|0x2 (binario 10)|
|TABLE_NAME|0x4 (binario 100)|
|TABLE_TYPE|0x8 (binario 1000)|

A continuación, hay un bit por cada restricción. Dado que desea admitir solo TABLE_NAME, se devolvería 0x4 en el elemento `rgRestrictions`. Si admite TABLE_CATALOG y TABLE_NAME, se devolvería 0x5 (binario 101).

De forma predeterminada, la implementación devuelve 0 (no admite ninguna restricción) para cualquier solicitud. UpdatePV es un ejemplo de un proveedor que sí admite restricciones.

### <a name="example"></a>Ejemplo

Este código se toma del ejemplo [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV). `UpdatePv` admite los tres conjuntos de filas de esquema requeridos: DBSCHEMA_TABLES, DBSCHEMA_COLUMNS y DBSCHEMA_PROVIDER_TYPES. Puede encontrar un ejemplo de cómo implementar la compatibilidad con el esquema en el proveedor en este tema, que incluye instrucciones para implementar el conjunto de filas DBSCHEMA_TABLE.

> [!NOTE]
> El código de ejemplo puede diferir de lo que se muestra aquí; se debe considerar como la versión más actualizada.

Es el primer paso para agregar compatibilidad con el esquema ES determinar qué restricciones se van a admitir. Con el fin de determinar qué restricciones estarán disponibles para el conjunto de filas de esquema, fíjese en la especificación OLE DB de la definición de `IDBSchemaRowset`. Después de la definición principal, verá una tabla que contiene el nombre del conjunto de filas de esquema, el número de restricciones y las columnas de restricción. Seleccione el conjunto de filas de esquema que desea admitir y anote el número de restricciones y las columnas de restricción. Por ejemplo, DBSCHEMA_TABLES admite cuatro restricciones (TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME y TABLE_TYPE):

```cpp
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,
   ULONG* rgRestrictions)
{
    for (ULONG l=0; l<cRestrictions; l++)
    {
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
            rgRestrictions[l] = 0x0C;
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))
                 rgRestrictions[l] = 0x04;
             else if (InlineIsEqualGUID(rguidSchema[l],
                                        DBSCHEMA_PROVIDER_TYPES))
                      rgRestrictions[l] = 0x00;
   }
}
```

Un bit representa cada columna de restricción. Si desea admitir una restricción (es decir, se pueden realizar consultas), establezca ese bit en 1. Si no desea admitir una restricción, establezca el valor en cero. En la línea de código anterior, `UpdatePV` admite las restricciones TABLE_NAME y TABLE_TYPE en el conjunto de filas DBSCHEMA_TABLES. Se trata de la tercera (máscara de bits 100) y la cuarta (máscara de bits 1000) restricción. Por lo tanto, la máscara de bits de `UpdatePv` es 1100 (o 0x0C):

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

La siguiente función `Execute` es similar a los conjuntos de filas normales. Tiene tres argumentos: *pcRowsAffected*, *cRestrictions* y *rgRestrictions*. La variable *pcRowsAffected* es un parámetro de salida con el que el proveedor puede devolver el recuento de filas en el conjunto de filas de esquema. El parámetro *cRestrictions* es un parámetro de entrada que contiene el número de restricciones que el consumidor pasa al proveedor. El parámetro *rgRestrictions* es una matriz de valores de tipo VARIANT que contienen los valores de restricción.

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

La variable *cRestrictions* se basa en el número total de restricciones de un conjunto de filas de esquema, independientemente de si el proveedor las admite. Dado que UpdatePv admite dos restricciones (la tercera y cuarta), este código solo busca un valor *cRestrictions* mayor o igual a tres.

El valor de la restricción TABLE_NAME se almacena en *rgRestrictions [2]* (de nuevo, la tercera restricción de una matriz basada en cero es 2). Compruebe que la restricción no es VT_EMPTY para admitirla realmente. Tenga en cuenta que VT_NULL no es igual a VT_EMPTY. VT_NULL especifica un valor de restricción válida.

La definición `UpdatePv` de un nombre de tabla es un nombre de ruta de acceso completa a un archivo de texto. Extraiga el valor de restricción y, a continuación, intente abrir el archivo para asegurarse de que existe realmente. Si el archivo no existe, se devuelve S_OK. Aunque pueda parecer un retroceso, lo que el código indica realmente al consumidor es que el nombre especificado no admitía ninguna tabla. El valor devuelto S_OK significa que el código se ejecutó correctamente.

```cpp
USES_CONVERSION;
enum {
            sizeOfszFile = 255
};
CTABLESRow  trData;
FILE        *pFile = NULL;
TCHAR       szFile[ sizeOfszFile ];
errcode     err = 0;

// Handle any restrictions sent to us. This only handles
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04
// for a total of (0x0C)
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)
{
    CComBSTR bstrName = rgRestrictions[2].bstrVal;
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))
    {
        // Check to see if the file exists
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));
        if (szFile[0] == _T('\0') ||
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))
        {
            return S_OK;// Their restriction was invalid return no data
        }
        else
        {
            fclose(pFile);
        }
    }
}
```

El proceso de admitir la cuarta restricción (TABLE_TYPE) es similar a la tercera. Compruebe que el valor no es VT_EMPTY. Esta restricción solo devuelve el tipo de tabla TABLE. Para determinar los valores válidos de DBSCHEMA_TABLES, busque **Apéndice B** en la **referencia del programador de OLE DB**, en la sección del conjunto de filas TABLES.

```cpp
// TABLE_TYPE restriction:
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)
{
    CComBSTR bstrType = rgRestrictions[3].bstrVal;
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))
    {
        // This is kind of a blind restriction.
        // This only actually supports
        // TABLES so if you get anything else,
        // just return an empty rowset.
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)
            return S_OK;
    }
}
```

Aquí es donde realmente crear una entrada de fila para el conjunto de filas. La variable `trData` corresponde a `CTABLESRow`, una estructura definida en las plantillas del proveedor OLE DB. `CTABLESRow` corresponde a la definición del conjunto de filas TABLES en el **apéndice B** de la especificación OLE DB. Solo tiene una fila para agregar porque solo puede admitir una tabla a la vez.

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` establece solo tres columnas: Table_name, TABLE_TYPE y DESCRIPTION. Anote las columnas para las que devolverá información, ya que necesitará esta información al implementar `GetDBStatus`:

```cpp
    _ATLTRY
    {
        m_rgRowData.Add(trData);
    }
    _ATLCATCHALL()
    {
        return E_OUTOFMEMORY;
    }
    //if (!m_rgRowData.Add(trData))
    //    return E_OUTOFMEMORY;
    *pcRowsAffected = 1;
    return S_OK;
}
```

La función `GetDBStatus` es importante para el correcto funcionamiento del conjunto de filas de esquema. Dado que no devuelve datos para cada columna del conjunto de filas TABLES, deberá especificar para qué columnas se devuelven datos y para cuáles no.

```cpp
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pColInfo != NULL);

    switch(pColInfo->iOrdinal)
    {
    case 3:     // TABLE_NAME
    case 4:     // TABLE_TYPE
    case 6:     // DESCRIPTION
        return DBSTATUS_S_OK;
        break;
    default:
        return DBSTATUS_S_ISNULL;
    break;
    }
}
```

Como la función `Execute` devuelve datos de los campos TABLE_NAME, TABLE_TYPE y DESCRIPTION del conjunto de filas TABLES, puede buscar en el **apéndice B** de la especificación OLE DB y determinar (contando desde arriba) que son ordinales 3, 4 y 6. Para cada una de esas columnas, devuelva DBSTATUS_S_OK. Para todas las demás columnas, devuelva DBSTATUS_S_ISNULL. Es importante devolver este estado, ya que un consumidor podría no comprender que el valor que devuelve es NULL o cualquier otro. Nuevamente, observe que NULL no es equivalente a un valor vacío.

Para obtener más información sobre la interfaz de conjunto de filas de esquema OLE DB, consulte la interfaz [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) en la **referencia del programador OLE DB**.

Para obtener información sobre cómo los consumidores pueden usar métodos `IDBSchemaRowset`, vea [Obtener metadatos con conjuntos de filas de esquema](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).

Si quiere ver un ejemplo de un proveedor que admite conjuntos de filas de esquema, vea el ejemplo [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV).

## <a name="see-also"></a>Vea también

[Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)
