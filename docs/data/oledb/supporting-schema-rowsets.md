---
title: Admitir conjuntos de filas de esquema
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: b49d53836179d765a72409d28304d7166dcf51d8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024626"
---
# <a name="supporting-schema-rowsets"></a>Admitir conjuntos de filas de esquema

Conjuntos de filas de esquema permiten a los consumidores obtener información acerca de un almacén de datos sin conocer su estructura subyacente, o esquema. Por ejemplo, un almacén de datos podría tener tablas organizadas en una jerarquía definida por el usuario, por lo que no habría ninguna manera de garantizar el conocimiento del esquema, excepto cuando lo lea. (Como otro ejemplo, los asistentes de Visual C++ usar conjuntos de filas de esquema para generar los descriptores de acceso para el consumidor). Para permitir que el consumidor hacer esto, el objeto de sesión del proveedor expone los métodos en el [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) interfaz. En las aplicaciones de Visual C++, usas la [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) clase implemente `IDBSchemaRowset`.

`IDBSchemaRowsetImpl` admite los siguientes métodos:

- [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) comprueba la validez de las restricciones en un conjunto de filas de esquema.

- [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) implementa una función de creador del objeto COM para el objeto especificado por el parámetro de plantilla.

- [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) especifica qué restricciones se admiten en un conjunto de filas de esquema determinado.

- [IDBSchemaRowset:: GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) devuelve un conjunto de filas de esquema (heredado de la interfaz).

- [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) devuelve una lista de conjuntos de filas de esquema accesibles por `IDBSchemaRowsetImpl::GetRowset` (heredado de la interfaz).

## <a name="atl-ole-db-provider-wizard-support"></a>Asistente para compatibilidad ATL OLE DB proveedor

El **el Asistente para proveedores OLE DB ATL** crea tres clases de esquema en el archivo de encabezado de sesión:

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

Estas clases responden a las solicitudes de consumidor de la información de esquema; Tenga en cuenta que la especificación OLE DB requiere que se admiten estos conjuntos de filas de tres esquema:

- **C**<em>ShortName</em>**SessionTRSchemaRowset** controla las solicitudes de información de la tabla (el conjunto de filas de esquema DBSCHEMA_TABLES).

- **C**<em>ShortName</em>**SessionColSchemaRowset** controla las solicitudes de información de columna (el conjunto de filas de esquema DBSCHEMA_COLUMNS). El asistente proporciona implementaciones de ejemplo para estas clases, que devuelven información de esquema para un proveedor de denegación de servicio.

- **C**<em>ShortName</em>**SessionPTSchemaRowset** controla las solicitudes de información de esquema sobre el tipo de proveedor (el conjunto de filas de esquema DBSCHEMA_PROVIDER_TYPES). La implementación predeterminada proporcionada por el asistente devuelve S_OK.

Puede personalizar estas clases para controlar la información de esquema apropiada para el proveedor:

- En **C**<em>ShortName</em>**SessionTRSchemaRowset**, debe rellenar los campos de catálogo, tabla y descripción (`trData.m_szType`, `trData.m_szTable`y `trData.m_szDesc`). El ejemplo generado por el asistente utiliza una única fila (tabla). Otros proveedores pueden devolver más de una tabla.

- En **C**<em>ShortName</em>**SessionColSchemaRowset**, pase el nombre de la tabla como un `DBID`.

## <a name="setting-restrictions"></a>Configuración de restricciones

Un concepto importante en la compatibilidad con el conjunto de filas de esquema es establecer restricciones, lo que hacer uso de `SetRestrictions`. Las restricciones permiten a los clientes obtener solo las filas coincidentes (por ejemplo, buscar todas las columnas de la tabla "MyTable"). Las restricciones son opcionales y, en caso de que no se admita ninguna (comportamiento predeterminado), se devuelven siempre todos los datos. Para obtener un ejemplo de un proveedor que admite restricciones, vea el [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) ejemplo.

## <a name="setting-up-the-schema-map"></a>Configurar la asignación de esquema

Configurar una asignación de esquema, como en el archivo Session.h de UpdatePV:

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

Para admitir `IDBSchemaRowset`, debe admitir DBSCHEMA_TABLES, DBSCHEMA_COLUMNS y DBSCHEMA_PROVIDER_TYPES. Puede agregar conjuntos de filas de esquema adicionales a su entera discreción.

Declarar una clase de conjunto de filas de esquema con un `Execute` método como `CUpdateSessionTRSchemaRowset` en `UpdatePV`:

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession` hereda de `IDBSchemaRowsetImpl`, por lo que tiene todos los métodos de control de restricciones. Uso de `CSchemaRowsetImpl`, declarar tres clases secundarias (se muestran en el mapa de esquema anterior): `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset`, y `CUpdateSessionPTSchemaRowset`. Cada una de estas clases secundarias tiene un `Execute` método que controla su conjunto de restricciones (criterios de búsqueda) correspondiente. Cada `Execute` método compara los valores de la *cRestrictions* y *rgRestrictions* parámetros. Vea la descripción de estos parámetros en [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).

Para obtener más información sobre qué restricciones corresponden a un conjunto de filas de esquema determinado, consulte la tabla del conjunto de filas de esquema GUID en [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) en el **referencia del programador de OLE DB** en el SDK de Windows .

Por ejemplo, si se admite la restricción TABLE_NAME en DBSCHEMA_TABLES, haría lo siguiente:

En primer lugar, busque DBSCHEMA_TABLES y vea si admite cuatro restricciones (en orden).

|Restricción del conjunto de filas de esquema|Valor de restricción|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0 x 1 (binario 1)|
|TABLE_SCHEMA|0 x 2 (binario 10)|
|TABLE_NAME|0 x 4 (binario 100)|
|TABLE_TYPE|0 x 8 (binario 1000)|

A continuación, hay un bit por cada restricción. Dado que desea admitir solo TABLE_NAME, devolvería 0 x 4 en el `rgRestrictions` elemento. Si admite TABLE_CATALOG y TABLE_NAME, devolvería 0 x 5 (binario 101).

De forma predeterminada, la implementación devuelve 0 (no admite ninguna restricción) para cualquier solicitud. UpdatePV es un ejemplo de un proveedor que admite restricciones.

### <a name="example"></a>Ejemplo

Este código se toma de la [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) ejemplo. `UpdatePv` admite los tres conjuntos de filas de esquema requerido: DBSCHEMA_TABLES, DBSCHEMA_COLUMNS y DBSCHEMA_PROVIDER_TYPES. Como ejemplo de cómo implementar la compatibilidad con el esquema en el proveedor, en este tema le guía para implementar el conjunto de filas DBSCHEMA_TABLE.

> [!NOTE]
> El código de ejemplo puede diferir de lo que se muestra aquí. el código de ejemplo se debe considerar como la versión más actualizada.

Es el primer paso para agregar compatibilidad con el esquema determinar qué restricciones que se va a admitir. Para determinar qué restricciones están disponibles para el conjunto de filas de esquema, fíjese en la especificación de OLE DB para la definición de `IDBSchemaRowset`. Después de la definición principal, verá una tabla que contiene el nombre del conjunto de filas de esquema, el número de restricciones y las columnas de restricción. Seleccione el conjunto de filas de esquema que desea admitir y tome nota del número de restricciones y las columnas de restricción. Por ejemplo, DBSCHEMA_TABLES admite cuatro restricciones (TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME y TABLE_TYPE):

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

Un bit representa cada columna de restricción. Si desea admitir una restricción (es decir, puede consultar por él), asigne el valor 1. Si no desea admitir una restricción, asigne el valor en cero. Desde la línea de código anterior, `UpdatePV` admite las restricciones TABLE_NAME y TABLE_TYPE en el conjunto de filas DBSCHEMA_TABLES. Se trata de la tercera (máscara de bits 100) y la cuarta restricciones (máscara de bits 1000). Por lo tanto, la máscara de bits `UpdatePv` es 1100 (o 0x0C):

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

La siguiente `Execute` función es similar a los conjuntos de filas normales. Tiene tres argumentos: *pcRowsAffected*, *cRestrictions*, y *rgRestrictions*. El *pcRowsAffected* variable es un parámetro de salida que el proveedor puede devolver el recuento de filas en el conjunto de filas de esquema. El *cRestrictions* parámetro es un parámetro de entrada que contiene el número de restricciones que se pasa por el consumidor al proveedor. El *rgRestrictions* parámetro es una matriz de valores de tipo VARIANT que contienen los valores de restricción.

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

El *cRestrictions* variable se basa en el número total de restricciones para un conjunto de filas de esquema, independientemente de si el proveedor admite. Dado que UpdatePv admite dos restricciones (la tercera y cuarta), este código solo busca un *cRestrictions* valor mayor o igual a tres.

El valor de la restricción TABLE_NAME se almacena en *rgRestrictions [2]* (de nuevo, la tercera restricción de una matriz basada en cero es 2). Compruebe que la restricción no es VT_EMPTY para admitirla realmente. Tenga en cuenta que VT_NULL no es igual a VT_EMPTY. VT_NULL especifica un valor de restricción válida.

El `UpdatePv` definición de un nombre de tabla es un nombre de ruta de acceso completa a un archivo de texto. Extraer el valor de restricción y, a continuación, intente abrir el archivo para asegurarse de que el archivo existe realmente. Si el archivo no existe, devuelve S_OK. Esto puede parecer un poco hacia atrás, pero realmente indica que el consumidor lo que el código es que no había ninguna tabla admitida por el nombre especificado. El valor devuelto S_OK significa que el código que se ejecutó correctamente.

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

Admitir la cuarta restricción (TABLE_TYPE) es similar a la restricción de terceros. Compruebe que el valor no es VT_EMPTY. Esta restricción solo devuelve el tipo de tabla, la tabla. Para determinar los valores válidos para DBSCHEMA_TABLES, busque **Apéndice B** de la **referencia del programador de OLE DB** en la sección del conjunto de filas de tablas.

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

Esto es donde realmente crear una entrada de fila para el conjunto de filas. La variable `trData` corresponde a `CTABLESRow`, una estructura definida en las plantillas de proveedor OLE DB. `CTABLESRow` corresponde a la definición del conjunto de filas de tablas en **Apéndice B** de la especificación de OLE DB. Solo tiene una fila para agregar porque solo puede admitir una tabla a la vez.

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` establece sólo tres columnas: Table_name, TABLE_TYPE y DESCRIPTION. Tome nota de las columnas que devuelve información, porque necesitará esta información al implementar `GetDBStatus`:

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

El `GetDBStatus` función es importante para el correcto funcionamiento del conjunto de filas de esquema. Dado que no devuelve datos para cada columna del conjunto de filas de tablas, deberá especificar qué columnas se devuelven datos de y cuáles no.

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

Dado que su `Execute` función devuelve datos para los campos TABLE_NAME, TABLE_TYPE y la descripción del conjunto de filas de tablas, puede buscar en **Apéndice B** de la especificación de OLE DB y determinar (contando de arriba) que son ordinales 3, 4 y 6. Para cada una de esas columnas, devuelva DBSTATUS_S_OK. Para todas las demás columnas, devuelva DBSTATUS_S_ISNULL. Es importante devolver este estado, ya que un consumidor no puede comprender que el valor que devuelva es NULL o alguna otra cosa. Nuevamente, observe que NULL no es equivalente a vacío.

Para obtener más información acerca de la interfaz de conjunto de filas de esquema OLE DB, consulte el [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) interfaz en el **referencia del programador de OLE DB**.

Para obtener información acerca de cómo los consumidores pueden usar `IDBSchemaRowset` métodos, vea [obtener metadatos con conjuntos de filas de esquema](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).

Para obtener un ejemplo de un proveedor que admite conjuntos de filas de esquema, vea el [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) ejemplo.

## <a name="see-also"></a>Vea también

[Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)
