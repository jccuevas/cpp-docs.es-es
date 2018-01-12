---
title: Admitir conjuntos de filas de esquema | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b981af06f48834eef59103b872b8b07e75cd0065
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-schema-rowsets"></a>Admitir conjuntos de filas de esquema
Conjuntos de filas de esquema que los consumidores puedan obtener información acerca de un almacén de datos sin conocer su estructura subyacente, o esquema. Por ejemplo, un almacén de datos podría tener tablas organizadas en una jerarquía definida por el usuario, por lo que no habría ninguna manera de asegurarse de conocimiento del esquema sin leerlo. (Como otro ejemplo, observe que los asistentes de Visual C++ utilizan conjuntos de filas de esquema para generar descriptores de acceso para el consumidor). Para permitir que el consumidor hacer esto, objeto de sesión del proveedor expone los métodos en el [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) interfaz. En las aplicaciones de Visual C++, usas la [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) clase para implementar **IDBSchemaRowset**.  
  
 `IDBSchemaRowsetImpl`admite los siguientes métodos:  
  
-   [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) comprueba la validez de las restricciones en un conjunto de filas de esquema.  
  
-   [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) implementa una función de creación de objeto COM para el objeto especificado por el parámetro de plantilla.  
  
-   [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) especifica qué restricciones se admiten en un conjunto de filas de esquema determinado.  
  
-   [IDBSchemaRowset:: GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) devuelve un conjunto de filas de esquema (que se hereda de la interfaz).  
  
-   [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) devuelve una lista de conjuntos de filas de esquema accesibles por `IDBSchemaRowsetImpl::GetRowset` (que se hereda de la interfaz).  
  
## <a name="atl-ole-db-provider-wizard-support"></a>Asistente para compatibilidad ATL OLE DB proveedor  
 El Asistente para proveedores OLE DB ATL crea tres clases de esquema en el archivo de encabezado de sesión:  
  
-   **C** *ShortName* **SessionTRSchemaRowset**  
  
-   **C** *ShortName* **SessionColSchemaRowset**  
  
-   **C** *ShortName* **SessionPTSchemaRowset**  
  
 Estas clases responden a las solicitudes de consumidor para obtener información de esquema; Tenga en cuenta que la especificación OLE DB requiere que estos conjuntos de filas de tres esquema sean compatibles:  
  
-   **C** *ShortName* **SessionTRSchemaRowset** administra las solicitudes de información de la tabla (la `DBSCHEMA_TABLES` de filas de esquema).  
  
-   **C** *ShortName* **SessionColSchemaRowset** administra las solicitudes de información de columna (la **DBSCHEMA_COLUMNS** de filas de esquema). El asistente proporciona implementaciones de ejemplo para estas clases, que devuelven información de esquema para un proveedor de DOS.  
  
-   **C** *ShortName* **SessionPTSchemaRowset** administra las solicitudes de información de esquema sobre el tipo de proveedor (el **DBSCHEMA_PROVIDER_TYPES** conjunto de filas de esquema). La implementación predeterminada proporcionada por el asistente devuelve `S_OK`.  
  
 Puede personalizar estas clases para controlar la información de esquema apropiada para el proveedor:  
  
-   En **C***ShortName***SessionTRSchemaRowset**, debe rellenar los campos de catálogo, tabla y descripción (**trData.m_szType**, **trData.m_szTable**, y **trData.m_szDesc**). El ejemplo generados por el asistente utiliza una sola fila (tabla). Otros proveedores pueden devolver más de una tabla.  
  
-   En **C***ShortName***SessionColSchemaRowset**, pase el nombre de la tabla como un **DBID**.  
  
## <a name="setting-restrictions"></a>Establecer restricciones  
 Un concepto importante en la compatibilidad de conjunto de filas de esquema es establecer restricciones, lo que hacer utilizando `SetRestrictions`. Las restricciones permiten a los clientes obtener solo las filas coincidentes (por ejemplo, buscar todas las columnas de la tabla "MyTable"). Las restricciones son opcionales y, en caso de que no se admita ninguna (comportamiento predeterminado), se devuelven siempre todos los datos. Para obtener un ejemplo de un proveedor que admite restricciones, vea el [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ejemplo.  
  
## <a name="setting-up-the-schema-map"></a>Cómo configurar la asignación de esquema  
 Configurar una asignación de esquema, como en el archivo Session.h de UpdatePV:  
  
```  
BEGIN_SCHEMA_MAP(CUpdateSession)  
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)  
END_SCHEMA_MAP()  
```  
  
 Para admitir **IDBSchemaRowset**, debe ser compatible con `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, y **DBSCHEMA_PROVIDER_TYPES**. Puede agregar conjuntos de filas de esquema adicional a su entera discreción.  
  
 Declarar una clase de conjunto de filas de esquema con un `Execute` método como `CUpdateSessionTRSchemaRowset` en UpdatePV:  
  
```  
class CUpdateSessionTRSchemaRowset :   
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,   
                              CTABLESRow, CUpdateSession >  
...  
// Execute looks like this; what pointers does the consumer use?  
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,   
                    ULONG cRestrictions, const VARIANT* rgRestrictions)  
```  
  
 Tenga en cuenta que `CUpdateSession` hereda de `IDBSchemaRowsetImpl`, por lo que tiene todos los métodos de control de restricciones. Usar `CSchemaRowsetImpl`, declarar tres clases secundarias (que se muestran en el mapa de esquema anterior): `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset`, y `CUpdateSessionPTSchemaRowset`. Cada una de estas clases secundarias tiene un `Execute` método que controla su conjunto de restricciones (criterios de búsqueda) correspondiente. Cada `Execute` método compara los valores de la `cRestrictions` y `rgRestrictions` parámetros. Vea la descripción de estos parámetros en [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
 Para obtener más información acerca de qué restricciones corresponden a un conjunto de filas de esquema determinado, consulte la tabla del conjunto de filas de esquema GUID en [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en el *referencia del programador de OLE DB* en el SDK de Windows.  
  
 Por ejemplo, si admite la **TABLE_NAME** restricción en `DBSCHEMA_TABLES`, podría hacer lo siguiente:  
  
 En primer lugar, buscar `DBSCHEMA_TABLES` y vea si admite cuatro restricciones (en orden).  
  
|Restricción de conjunto de filas de esquema|Valor de restricción|  
|-------------------------------|-----------------------|  
|**TABLE_CATALOG**|0 x 1 (binario 1)|  
|**TABLE_SCHEMA**|0 x 2 (binario 10)|  
|**TABLE_NAME**|0 x 4 (binario 100)|  
|**TABLE_TYPE**|0 x 8 (binario 1000)|  
  
 A continuación, tenga en cuenta que hay un bit por cada restricción. Dado que desea admitir **TABLE_NAME** solo, devolvería 0 x 4 en el `rgRestrictions` elemento. Si admite **TABLE_CATALOG** y **TABLE_NAME**, se devolvería 0 x 5 (binario 101).  
  
 De forma predeterminada, la implementación devuelve 0 (no admite ninguna restricción) para cualquier solicitud. UpdatePV es un ejemplo de un proveedor que admite restricciones.  
  
### <a name="example"></a>Ejemplo  
 Este código se toma de la [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ejemplo. UpdatePv admite los tres conjuntos de filas de esquema requeridos: `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, y **DBSCHEMA_PROVIDER_TYPES**. Como ejemplo de cómo implementar la compatibilidad con el esquema en un proveedor, este tema le guía para implementar el **DBSCHEMA_TABLE** conjunto de filas.  
  
> [!NOTE]
>  El código de ejemplo puede diferir de lo que se muestre aquí; el ejemplo de código se debe considerar como la versión más actualizada.  
  
 El primer paso para agregar compatibilidad con esquemas es determinar qué restricciones se va a admitir. Para determinar las restricciones que están disponibles para el conjunto de filas de esquema, examine la especificación de OLE DB para la definición de **IDBSchemaRowset**. Después de la definición principal, verá una tabla que contiene el nombre del conjunto de filas de esquema, el número de restricciones y las columnas de restricción. Seleccione el conjunto de filas de esquema que desea admitir y tome nota del número de restricciones y las columnas de restricción. Por ejemplo, `DBSCHEMA_TABLES` admite cuatro restricciones (**TABLE_CATALOG**, **TABLE_SCHEMA**, **TABLE_NAME**, y **TABLE_TYPE** ):  
  
```  
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
  
 Un bit representa cada columna de restricción. Si desea admitir una restricción (es decir, puede realizar consultas en él), establezca ese bit en 1. Si no desea admitir una restricción, establezca ese bit en cero. Desde la línea de código anterior, UpdatePV admite la **TABLE_NAME** y **TABLE_TYPE** restricciones en la `DBSCHEMA_TABLES` conjunto de filas. Se trata de la tercera (máscara de bits 100) y la cuarta restricciones (máscara de bits 1000). Por lo tanto, la máscara de bits para UpdatePv es 1100 (ó 0x0C):  
  
```  
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
    rgRestrictions[l] = 0x0C;  
```  
  
 El siguiente `Execute` función es similar a los conjuntos de filas normales. Tiene tres argumentos: `pcRowsAffected`, `cRestrictions`, y `rgRestrictions`. El `pcRowsAffected` variable es un parámetro de salida que el proveedor puede devolver el recuento de filas en el conjunto de filas de esquema. El `cRestrictions` parámetro es un parámetro de entrada que contiene el número de restricciones pasadas por el consumidor al proveedor. El `rgRestrictions` parámetro es una matriz de **VARIANT** valores que contienen los valores de restricción.  
  
```  
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,   
                const VARIANT* rgRestrictions)  
```  
  
 El `cRestrictions` variable se basa en el número total de restricciones para un conjunto de filas de esquema, independientemente de si el proveedor admite. Puesto que UpdatePv admite dos restricciones (la tercera y cuarta), este código sólo busca un `cRestrictions` valor mayor o igual que tres.  
  
 El valor de la **TABLE_NAME** restricción se almacena en `rgRestrictions[2]` (de nuevo, la tercera restricción de una matriz basada en cero es 2). Deberá comprobar que la restricción no es `VT_EMPTY` para admitirla realmente. Tenga en cuenta que **VT_NULL** no es igual a `VT_EMPTY`. **VT_NULL** especifica un valor de restricción válida.  
  
 La definición UpdatePv de un nombre de tabla es un nombre de ruta de acceso completa a un archivo de texto. Extraer el valor de restricción y, a continuación, intente abrir el archivo para asegurarse de que el archivo existe realmente. Si el archivo no existe, devuelve `S_OK`. Esto puede parecer un poco hacia atrás, pero lo que el código indica realmente al consumidor es que no había ninguna tabla admitida por el nombre especificado. El `S_OK` retorno significa que el código que se ejecutó correctamente.  
  
```  
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
  
 Admitir la cuarta restricción (**TABLE_TYPE**) es similar a la tercera restricción. Compruebe que el valor no es `VT_EMPTY`. Esta restricción sólo devuelve el tipo de tabla, **tabla**. Para determinar los valores válidos para la `DBSCHEMA_TABLES`, busque en el apéndice B de la *referencia del programador de OLE DB* en el **tablas** sección del conjunto de filas.  
  
```  
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
  
 Esto es donde se crea realmente una entrada de fila para el conjunto de filas. La variable `trData` corresponde a **CTABLESRow**, una estructura definida en las plantillas de proveedor OLE DB. **CTABLESRow** corresponde a la **tablas** definición de conjunto de filas en el apéndice B de la especificación de OLE DB. Sólo tiene una fila para agregar porque solo puede admitir una tabla a la vez.  
  
```  
// Bring over the data:  
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);  
wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);  
wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());  
```  
  
 UpdatePV sólo establece tres columnas: **TABLE_NAME**, **TABLE_TYPE**, y **descripción**. Debe realizar una nota de las columnas para las que devuelve información, ya que necesitará esta información al implementar `GetDBStatus`:  
  
```  
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
  
 El `GetDBStatus` función es muy importante para el correcto funcionamiento del conjunto de filas de esquema. Como no devuelve datos para cada columna de la **tablas** conjunto de filas, debe especificar qué columnas se devuelven datos de y cuáles no.  
  
```  
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
  
 Dado que su `Execute` función devuelve datos para el **TABLE_NAME**, **TABLE_TYPE**, y **descripción** campos desde el **tablas**conjunto de filas, puede buscar en el apéndice B de la especificación de OLE DB y determinar (contando de arriba hacia abajo) que son los ordinales 3, 4 y 6. Para cada una de esas columnas, devuelva **DBSTATUS_S_OK**. Para todas las demás columnas, devuelva **DBSTATUS_S_ISNULL**. Es importante devolver este estado, ya que un consumidor no puede comprender que es el valor que devuelva **NULL** u otra cosa. Una vez más, observe que **NULL** no es equivalente a vacía.  
  
 Para obtener más información acerca de la interfaz de conjunto de filas de esquema OLE DB, vea el [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) interfaz en la referencia de la base de datos del programador de OLE.  
  
 Para obtener información acerca de cómo pueden usar los consumidores **IDBSchemaRowset** métodos, vea [obtener metadatos con conjuntos de filas de esquema](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).  
  
 Para obtener un ejemplo de un proveedor que admite conjuntos de filas de esquema, consulte el [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)