---
title: "Admitir conjuntos de filas de esquema | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plantillas de consumidor OLE DB, conjuntos de filas de esquema"
  - "proveedores OLE DB, conjuntos de filas de esquema"
  - "OLE DB, conjuntos de filas de esquema"
  - "conjuntos de filas de esquema"
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Admitir conjuntos de filas de esquema
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los conjuntos de filas de esquema permiten a los consumidores obtener información acerca de un almacén de datos si conoce su estructura subyacente, o esquema.  Por ejemplo, un almacén de datos puede tener las tablas organizadas en una jerarquía definida por el usuario, por lo que no habría forma de garantizar el conocimiento del esquema sin leerlo. Como otro ejemplo, observe que los asistentes de Visual C\+\+ utilizan conjuntos de filas de esquema para generar descriptores de acceso para el consumidor. Para permitir al consumidor hacer esto, el objeto de sesión del proveedor expone los métodos en la interfaz [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx).  En las aplicaciones de Visual C\+\+ se utiliza la clase [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) para implementar **IDBSchemaRowset**.  
  
 `IDBSchemaRowsetImpl` admite los métodos siguientes:  
  
-   [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) comprueba la validez de las restricciones en un conjunto de filas de esquema.  
  
-   [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) implementa una función de creación de objeto COM para el objeto especificado por el parámetro de plantilla.  
  
-   [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) especifica qué restricciones se admiten en un conjunto de filas de esquema determinado.  
  
-   [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) devuelve un conjunto de filas de esquema \(heredado de la interfaz\).  
  
-   [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) devuelve una lista de conjuntos de filas de esquema, accesibles para `IDBSchemaRowsetImpl::GetRowset` \(heredado de la interfaz\).  
  
## Compatibilidad con el Asistente para proveedores OLE DB ATL  
 El Asistente para proveedores OLE DB ATL crea tres clases de esquema en el archivo de encabezado de sesión:  
  
-   **C** *Nombre\_corto* **SessionTRSchemaRowset**  
  
-   **C** *Nombre\_corto* **SessionColSchemaRowset**  
  
-   **C** *Nombre\_corto* **SessionPTSchemaRowset**  
  
 Estas clases responden a las solicitudes de información sobre el esquema realizadas por el consumidor; tenga en cuenta que la especificación de OLE DB requiere que se admitan los tres conjuntos de filas de esquema siguientes:  
  
-   **C** *Nombre\_corto* **SessionTRSchemaRowset** controla las solicitudes de información de tablas \(el conjunto de filas de esquema `DBSCHEMA_TABLES`\).  
  
-   **C** *Nombre\_corto* **SessionColSchemaRowset** controla las solicitudes de información de columnas \(el conjunto de filas de esquema **DBSCHEMA\_COLUMNS**\).  El asistente suministra implementaciones de ejemplo para estas clases, que devuelven información de esquema para un proveedor de DOS.  
  
-   **C** *Nombre\_corto* **SessionPTSchemaRowset** controla las solicitudes de información de esquema sobre el tipo de proveedor \(el conjunto de filas de esquema **DBSCHEMA\_PROVIDER\_TYPES**\).  La implementación predeterminada proporcionada por el asistente devuelve `S_OK`.  
  
 Puede personalizar estas clases para controlar la información de esquema apropiada para el proveedor:  
  
-   En **C***Nombre\_corto***SessionTRSchemaRowset**, debe rellenar los campos de catálogo, tabla y descripción \(**trData.m\_szType**, **trData.m\_szTable** y **trData.m\_szDesc**\).  El ejemplo generado por el asistente sólo utiliza una fila \(tabla\).  Otros proveedores pueden devolver varias tablas.  
  
-   En **C***Nombre\_corto***SessionColSchemaRowset**, debe pasar el nombre de la tabla como un identificador **DBID**.  
  
## Establecer restricciones  
 Un concepto importante en un conjunto de filas de esquema es establecer restricciones, lo que se hace mediante `SetRestrictions`.  Las restricciones permiten a los consumidores buscar únicamente las fichas coincidentes \(por ejemplo, buscar todas las columnas de la tabla "MyTable"\).  Las restricciones son opcionales y, en caso de que no se admita ninguna \(comportamiento predeterminado\), se devuelven siempre todos los datos.  Si desea examinar un ejemplo de proveedor que admite restricciones, vea el ejemplo [UpdatePV](http://msdn.microsoft.com/es-es/c8bed873-223c-4a7d-af55-f90138c6f38f).  
  
## Configurar el mapa de esquema  
 Configure un mapa de esquema como el siguiente, incluido en el archivo Session.h de UpdatePV:  
  
```  
BEGIN_SCHEMA_MAP(CUpdateSession)  
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)  
END_SCHEMA_MAP()  
```  
  
 Para ofrecer compatibilidad con **IDBSchemaRowset**, debe ofrecer compatibilidad con `DBSCHEMA_TABLES`, **DBSCHEMA\_COLUMNS** y **DBSCHEMA\_PROVIDER\_TYPES**.  Puede agregar los conjuntos de filas de esquema adicionales que desee.  
  
 Declare una clase de conjunto de filas con un método `Execute`, como `CUpdateSessionTRSchemaRowset`, en UpdatePV:  
  
```  
class CUpdateSessionTRSchemaRowset :   
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,   
                              CTABLESRow, CUpdateSession >  
...  
// Execute looks like this; what pointers does the consumer use?  
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,   
                    ULONG cRestrictions, const VARIANT* rgRestrictions)  
```  
  
 Tenga en cuenta que `CUpdateSession` hereda de `IDBSchemaRowsetImpl`, por lo que tiene todos los métodos de control de restricciones.  Utilice `CSchemaRowsetImpl` para declarar tres clases secundarias \(citadas en el mapa de esquema anterior\): `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset`, `CUpdateSessionPTSchemaRowset`.  Cada una de estas clases secundarias tiene un método `Execute` que controla su conjunto de restricciones correspondiente \(criterios de búsqueda\).  Cada método `Execute` compara los valores de los parámetros `cRestrictions` y `rgRestrictions`.  Vea la descripción de estos parámetros en [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
 Para obtener más información acerca de qué restricciones corresponden a un conjunto de filas de esquema determinado, consulte la tabla de GUID del conjunto de filas de esquema incluida en [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx), en la *Referencia del programador de OLE DB* de [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)].  
  
 Por ejemplo, si admite la restricción **TABLE\_NAME** en `DBSCHEMA_TABLES`, debe hacer lo siguiente:  
  
 En primer lugar, busque `DBSCHEMA_TABLES` y vea si admite cuatro restricciones \(por orden\).  
  
|Restricción de conjunto de filas de esquema|Valores de la restricción|  
|-------------------------------------------------|-------------------------------|  
|**TABLE\_CATALOG**|0x1 \(binario 1\)|  
|**TABLE\_SCHEMA**|0x2 \(binario 10\)|  
|**TABLE\_NAME**|0x4 \(binario 100\)|  
|**TABLE\_TYPE**|0x8 \(binario 1000\)|  
  
 A continuación, observe que hay un bit para cada restricción.  Como desea ofrecer compatibilidad con **TABLE\_NAME** únicamente, debe devolver 0x4 en el elemento `rgRestrictions`.  Si admite **TABLE\_CATALOG** y **TABLE\_NAME**, debe devolver 0x5 \(binario 101\).  
  
 De manera predeterminada, la implementación devuelve 0 \(no admite ninguna restricción\) para cualquier solicitud.  UpdatePV es un ejemplo de proveedor que admite restricciones.  
  
### Ejemplo  
 Este código se extrae del ejemplo [UpdatePV](http://msdn.microsoft.com/es-es/c8bed873-223c-4a7d-af55-f90138c6f38f).  UpdatePv admite los tres conjuntos de filas de esquema requeridos: `DBSCHEMA_TABLES`, **DBSCHEMA\_COLUMNS** y **DBSCHEMA\_PROVIDER\_TYPES**.  Como ejemplo de método para implementar la compatibilidad con esquemas en el proveedor, este tema le guía para implementar el conjunto de filas **DBSCHEMA\_TABLE**.  
  
> [!NOTE]
>  El código del ejemplo puede ser diferente del mostrado aquí; debe considerar el código del ejemplo como la versión más actualizada.  
  
 El primer paso para agregar compatibilidad con esquemas es determinar para qué restricciones se va a ofrecer compatibilidad.  Para determinar las restricciones que están disponibles para el conjunto de filas de esquema, consulte la definición de **IDBSchemaRowset** en la especificación de OLE DB.  Después de la definición principal, aparece una tabla que contiene el nombre del conjunto de filas de esquema, el número de restricciones y las columnas de restricción.  Seleccione el conjunto de filas de esquema para el que desee proporcionar compatibilidad y anote el número de restricciones y las columnas de restricción.  Por ejemplo, `DBSCHEMA_TABLES` admite cuatro restricciones \(**TABLE\_CATALOG**, **TABLE\_SCHEMA**, **TABLE\_NAME** y **TABLE\_TYPE**\):  
  
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
  
 Cada columna de restricción se representa mediante un bit.  Si desea admitir una restricción \(es decir, poder realizar consultas teniéndola en cuenta\), asigne el valor 1 a ese bit.  En caso contrario, asigne el valor 0.  Mediante la línea de código anterior, UpdatePV admite las restricciones **TABLE\_NAME** y **TABLE\_TYPE** en el conjunto de filas `DBSCHEMA_TABLES`.  Equivalen a la tercera restricción \(máscara de bits 100\) y la cuarta restricción \(máscara de bits 1000\).  Por tanto, la máscara de bits para UpdatePv es 1100 \(ó 0x0C\):  
  
```  
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
    rgRestrictions[l] = 0x0C;  
```  
  
 La siguiente función `Execute` es similar a las funciones de los conjuntos de filas normales.  Tiene tres argumentos: `pcRowsAffected`, `cRestrictions` y `rgRestrictions`.  La variable `pcRowsAffected` es un parámetro de salida que el proveedor puede devolver con el número de filas del conjunto de filas de esquema.  El parámetro `cRestrictions` es un parámetro de entrada que contiene el número de restricciones pasadas por el consumidor al proveedor.  El parámetro `rgRestrictions` es una matriz de valores de tipo **VARIANT** que contiene los valores de las restricciones.  
  
```  
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,   
                const VARIANT* rgRestrictions)  
```  
  
 La variable `cRestrictions` se basa en el número total de restricciones para un conjunto de filas de esquema, independientemente de si el proveedor las admite o no.  Puesto que UpdatePv admite dos restricciones \(la tercera y la cuarta\), este código sólo busca un valor de `cRestrictions` mayor o igual que tres.  
  
 El valor de la restricción **TABLE\_NAME** se almacena en `rgRestrictions[2]` \(de nuevo, la tercera restricción de una matriz basada en cero es 2\).  Tiene que comprobar que la restricción no es `VT_EMPTY` para admitirla realmente.  Tenga en cuenta que **VT\_NULL** no es igual a `VT_EMPTY`.  **VT\_NULL** especifica un valor de restricción válido.  
  
 La definición UpdatePv de un nombre de tabla es el nombre de la ruta de archivo completa de un archivo de texto.  Extraiga el valor de la restricción y después intente abrir el archivo para asegurarse de que el archivo existe realmente.  Si el archivo no existe, devuelve `S_OK`.  Esto puede parecer un poco al revés en cierto modo, pero lo que el código indica realmente al consumidor es que no había tablas compatibles con el nombre especificado.  El valor devuelto, `S_OK`, significa que el código se ejecutó correctamente.  
  
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
  
 El resultado de admitir la cuarta restricción \(**TABLE\_TYPE**\) es similar a utilizar la tercera.  Compruebe que el valor no es `VT_EMPTY`.  Esta restricción sólo devuelve el tipo de la tabla, **TABLE**.  Para determinar los valores válidos para `DBSCHEMA_TABLES`, busque en el Apéndice B de la *Referencia del programador de OLE DB*, en la sección del conjunto de filas **TABLES**.  
  
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
  
 Es aquí donde se crea realmente una entrada de fila para el conjunto de filas.  La variable `trData` corresponde a **CTABLESRow**, una estructura definida en las plantillas de proveedor OLE DB.  **CTABLESRow** corresponde a la definición del conjunto de filas **TABLES** incluida en el Apéndice B de la especificación de OLE DB.  Sólo tiene una fila para agregar, ya que sólo puede admitir una tabla cada vez.  
  
```  
// Bring over the data:  
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);  
wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);  
wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());  
```  
  
 UpdatePV sólo establece tres columnas: **TABLE\_NAME**, **TABLE\_TYPE** y **DESCRIPTION**.  Debe anotar las columnas para las que devuelve información, ya que necesita estos datos para implementar `GetDBStatus`:  
  
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
  
 La función `GetDBStatus` es muy importante para el correcto funcionamiento del conjunto de filas de esquema.  Como no devuelve datos para cada columna del conjunto de filas **TABLES**, debe especificar para qué columnas devuelve datos y para cuáles no.  
  
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
  
 Como la función `Execute` devuelve datos para los campos **TABLE\_NAME**, **TABLE\_TYPE** y **DESCRIPTION** del conjunto de filas **TABLES**, puede consultar el Apéndice B de la especificación de OLE DB y determinar \(contando de arriba a abajo\) que son los ordinales 3, 4 y 6.  Para cada una de esas columnas, devuelva **DBSTATUS\_S\_OK**.  Para todas las demás columnas, devuelva **DBSTATUS\_S\_ISNULL**.  Es importante devolver este estado, ya que un consumidor puede no comprender que el valor que devuelva sea **NULL** o de otro tipo.  Aquí también, tenga en cuenta que **NULL** no es equivalente a valor en blanco.  
  
 Para obtener más información acerca de la interfaz de conjuntos de filas de esquema OLE DB, vea la interfaz [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) en la Referencia del programador de OLE DB.  
  
 Para obtener más información sobre cómo pueden utilizar los consumidores los métodos **IDBSchemaRowset**, vea [Obtener metadatos con conjuntos de filas de esquema](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).  
  
 Si desea examinar un ejemplo de proveedor que admite conjuntos de filas de esquema, vea el ejemplo [UpdatePV](http://msdn.microsoft.com/es-es/c8bed873-223c-4a7d-af55-f90138c6f38f).  
  
## Vea también  
 [Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)