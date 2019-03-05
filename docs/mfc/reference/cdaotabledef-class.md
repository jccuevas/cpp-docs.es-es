---
title: CDaoTableDef (clase)
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
ms.openlocfilehash: 485fe3533916e5e59bc87084f58acfb37368ac32
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270233"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef (clase)

Representa la definición almacenada de una tabla base o una tabla asociada.

## <a name="syntax"></a>Sintaxis

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Construye un objeto `CDaoTableDef`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoTableDef::Append](#append)|Agrega una nueva tabla a la base de datos.|
|[CDaoTableDef::CanUpdate](#canupdate)|Devuelve cero si se puede actualizar la tabla (se puede modificar la definición de campos o propiedades de la tabla).|
|[CDaoTableDef::Close](#close)|Cierra una definición de tabla abierta.|
|[CDaoTableDef::Create](#create)|Crea una tabla que se puede agregar a la base de datos mediante [Append](#append).|
|[CDaoTableDef::CreateField](#createfield)|Se llama para crear un campo de una tabla.|
|[CDaoTableDef::CreateIndex](#createindex)|Se llama para crear un índice de una tabla.|
|[CDaoTableDef::DeleteField](#deletefield)|Se llama para eliminar un campo de una tabla.|
|[CDaoTableDef::DeleteIndex](#deleteindex)|Se llama para eliminar un índice de una tabla.|
|[CDaoTableDef::GetAttributes](#getattributes)|Devuelve un valor que indica una o varias características de un `CDaoTableDef` objeto.|
|[CDaoTableDef::GetConnect](#getconnect)|Devuelve un valor que proporciona información sobre el origen de una tabla.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Devuelve la fecha y hora de la tabla base subyacente un `CDaoTableDef` se creó el objeto.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha y hora de los cambios más recientes realizados en el diseño de la tabla base.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Devuelve un valor que representa el número de campos de la tabla.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Devuelve los tipos de información sobre los campos específicos en la tabla.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Devuelve el número de índices de la tabla.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Devuelve los tipos concretos de información sobre los índices de la tabla.|
|[CDaoTableDef::GetName](#getname)|Devuelve el nombre definido por el usuario de la tabla.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Devuelve el número de registros en la tabla.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Devuelve un valor que especifica el nombre de la tabla asociada en la base de datos de origen.|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Devuelve un valor que valida los datos de un campo cuando se cambia o se agregan a una tabla.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Devuelve un valor que especifica el texto del mensaje que la aplicación muestra si el valor de un objeto de campo no cumple la regla de validación especificado.|
|[CDaoTableDef::IsOpen](#isopen)|Devuelve distinto de cero si la tabla está abierto.|
|[CDaoTableDef::Open](#open)|Se abre una definición de tabla existente almacenado en la base de datos 's colección de definición de tabla.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Actualiza la información de conexión para una tabla asociada.|
|[CDaoTableDef::SetAttributes](#setattributes)|Establece un valor que indica una o varias características de un `CDaoTableDef` objeto.|
|[CDaoTableDef::SetConnect](#setconnect)|Establece un valor que proporciona información sobre el origen de una tabla.|
|[CDaoTableDef::SetName](#setname)|Establece el nombre de la tabla.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Establece un valor que especifica el nombre de una tabla asociada en la base de datos de origen.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Establece un valor que valida los datos de un campo cuando se cambia o se agregan a una tabla.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Establece un valor que especifica el texto del mensaje que la aplicación muestra si el valor de un objeto de campo no cumple la regla de validación especificado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Un puntero a la interfaz DAO subyacente al objeto de definición de tabla.|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Base de datos de origen para esta tabla.|

## <a name="remarks"></a>Comentarios

Cada objeto de base de datos DAO mantiene una colección, denominada definiciones de tabla, que contiene todos los objetos de definición de tabla DAO guardados.

Manipular una definición de tabla mediante una `CDaoTableDef` objeto. Por ejemplo, se puede:

- Examinar la estructura de campo y el índice de cualquier tabla local, adjunta o externa en una base de datos.

- Llamar a la `SetConnect` y `SetSourceTableName` funciones miembro para las tablas asociadas y use el `RefreshLink` función miembro para actualizar las conexiones a tablas asociadas.

- Llame a la `CanUpdate` para determinar si se pueden editar las definiciones de campo en la tabla de función miembro.

- Obtiene o establece las condiciones de validación mediante el `GetValidationRule` y `SetValidationRule`y el `GetValidationText` y `SetValidationText` funciones miembro.

- Use la `Open` función miembro para crear una tabla, Dynaset o tipo de instantánea `CDaoRecordset` objeto.

    > [!NOTE]
    >  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". También puede seguir acceso a orígenes de datos ODBC con las clases DAO; las clases DAO normalmente ofrecen capacidades superior porque son específicas para el motor de base de datos Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Usar objetos de definición de tabla para trabajar con una tabla existente o crear una nueva tabla

1. En todos los casos, construir un `CDaoTableDef` objeto, que se suministra un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto al que pertenece la tabla.

1. A continuación, haga lo siguiente, según lo que desee:

   - Para utilizar una existente que se ha guardado la tabla, llame al objeto de definición de tabla [abierto](#open) función miembro, proporcionando el nombre de la tabla guardada.

   - Para crear una nueva tabla, llame el objeto de definición de tabla [crear](#create) función miembro, proporcionando el nombre de la tabla. Llame a [CreateField](#createfield) y [CreateIndex](#createindex) para agregar campos y los índices para la tabla.

   - Llame a [Append](#append) para guardar la tabla agregando a la colección de definiciones de tabla de la base de datos. `Create` coloca la definición de tabla en un estado abierto, por lo que después de llamar a `Create` no llame a `Open`.

        > [!TIP]
        >  Es la manera más fácil de crear tablas guardadas crearlos y almacenarlos en la base de datos con Microsoft Access. A continuación, puede abrir y usarlos en el código MFC.

Para usar el objeto de definición de tabla abre o se crea, crear y abrir un `CDaoRecordset` objeto, especificando el nombre de la definición de tabla con un `dbOpenTable` valor en el *nOpenType* parámetro.

Usar un objeto de definición de tabla para crear un `CDaoRecordset` de objeto, se suelen crear o abre una definición de tabla, como se describió anteriormente y luego construya un objeto de conjunto de registros, pasando un puntero al objeto de definición de tabla al llamar a [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). La definición de tabla que se pasa debe estar en un estado abierto. Para obtener más información, vea la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Cuando termine de utilizar un objeto de definición de tabla, llame a su [cerrar](../../mfc/reference/cdaorecordset-class.md#close) miembro de función; a continuación, destruya el objeto de definición de tabla.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

##  <a name="append"></a>  CDaoTableDef::Append

Llame a esta función miembro después de llamar a [crear](#create) para crear un nuevo objeto de definición de tabla para guardar la definición de tabla en la base de datos.

```
virtual void Append();
```

### <a name="remarks"></a>Comentarios

La función anexa el objeto a la colección de definiciones de tabla de la base de datos. Puede usar la definición de tabla como un objeto temporal al definirla anexando No, pero si desea guardar y usarlo, debe llamar a `Append`.

> [!NOTE]
>  Si intenta agregar una definición de tabla sin nombre (que contiene una cadena nula o vacía), MFC inicia una excepción.

Para obtener información relacionada, vea el tema "Método Append" en la Ayuda de DAO.

##  <a name="canupdate"></a>  CDaoTableDef::CanUpdate

Llame a esta función miembro para determinar si la definición de la tabla subyacente un `CDaoTableDef` se puede cambiar el objeto.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se puede modificar la estructura de tabla (esquema) (Agregar o eliminar campos e índices), en caso contrario, 0.

### <a name="remarks"></a>Comentarios

De forma predeterminada, una tabla recién creada subyacente un `CDaoTableDef` se puede actualizar el objeto y una tabla asociada subyacente un `CDaoTableDef` objeto no se puede actualizar. Un `CDaoTableDef` objeto puede ser actualizable, incluso si el conjunto de registros resultante no es actualizable.

Para obtener información relacionada, vea el tema "Propiedad actualizable" en la Ayuda de DAO.

##  <a name="cdaotabledef"></a>  CDaoTableDef::CDaoTableDef

Construye un objeto `CDaoTableDef`.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parámetros

*pDatabase*<br/>
Un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.

### <a name="remarks"></a>Comentarios

Después de crear el objeto, se debe llamar a la [crear](#create) o [abierto](#open) función miembro. Cuando termine con el objeto, debe llamar a su [cerrar](#close) miembro de función y destruir el `CDaoTableDef` objeto.

##  <a name="close"></a>  CDaoTableDef::Close

Llame a esta función miembro para cerrar y liberar el objeto de definición de tabla.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Normalmente, después de llamar a `Close`, eliminar el objeto de definición de tabla si se ha asignado con **nuevo**.

Puede llamar a [abierto](#open) nuevamente después de llamar a `Close`. Esto permite reutilizar el objeto de definición de tabla.

Para obtener información relacionada, vea el tema "Método Close" en la Ayuda de DAO.

##  <a name="create"></a>  CDaoTableDef::Create

Llame a esta función miembro para crear una nueva tabla guardada.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una cadena que contiene el nombre de la tabla.

*lAttributes*<br/>
Un valor correspondiente a las características de la tabla representada por el objeto de definición de tabla. Puede usar la operación bit a bit OR para combinar cualquiera de las siguientes constantes:

|Constante|Descripción|
|--------------|-----------------|
|`dbAttachExclusive`|Para las bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que la tabla es una tabla asociada abierta para uso exclusivo.|
|`dbAttachSavePWD`|Para las bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que el Id. de usuario y la contraseña para la tabla asociada se guardan con la información de conexión.|
|`dbSystemObject`|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet.|
|`dbHiddenObject`|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet.|

*lpszSrcTable*<br/>
Un puntero a una cadena que contiene el nombre de la tabla de origen. De forma predeterminada, este valor se inicializa como NULL.

*lpszConnect*<br/>
Un puntero a una cadena que contiene la cadena de conexión predeterminada. De forma predeterminada, este valor se inicializa como NULL.

### <a name="remarks"></a>Comentarios

Una vez que haya asignado un nombre la definición de tabla, puede llamar [Append](#append) para guardar la definición de tabla en la colección de definiciones de tabla de la base de datos. Después de llamar a `Append`, la definición de tabla está en un estado abierto y se puede usar para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto.

Para obtener información relacionada, vea el tema "Método CreateTableDef" en la Ayuda de DAO.

##  <a name="createfield"></a>  CDaoTableDef::CreateField

Llame a esta función miembro para agregar un campo a la tabla.

```
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una expresión de cadena que especifica el nombre de este campo.

*nType*<br/>
Un valor que indica el tipo de datos del campo. El valor puede ser uno de estos valores:

|Tipo|Tamaño (bytes)|Descripción|
|----------|--------------------|-----------------|
|`dbBoolean`|1 byte|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|Moneda ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Fecha y hora ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Text ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Binario largo (objeto OLE), [CLongBinary](../../mfc/reference/clongbinary-class.md) o [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Memo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Un valor que indica el tamaño máximo, en bytes, de un campo que contiene el texto, o el tamaño de un campo que contiene valores numéricos o de texto fijo. El *lSize* parámetro se omite para todos, excepto los campos de texto.

*lAttributes*<br/>
Un valor que corresponde a las características del campo y se puede combinar con una operación bit a bit OR.

|Constante|Descripción|
|--------------|-----------------|
|`dbFixedField`|El tamaño del campo es fijo (valor predeterminado para los campos numéricos).|
|`dbVariableField`|El tamaño del campo es variable (sólo campos de texto).|
|`dbAutoIncrField`|El valor del campo para los nuevos registros se incrementa automáticamente a un único entero largo que no se puede cambiar. Solo se admite para las tablas de base de datos Microsoft Jet.|
|`dbUpdatableField`|Se puede cambiar el valor del campo.|
|`dbDescending`|El campo se ordena en orden descendente (Z - A 0 -100) orden (se aplica solo a un objeto de campo en una colección de campos de un objeto de índice). Si se omite esta constante, el campo se ordena en orden ascendente (A - Z o 0 - 100) orden (valor predeterminado).|

*fieldinfo*<br/>
Una referencia a un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura.

### <a name="remarks"></a>Comentarios

Un `DAOField` se crea y se anexa a la colección de campos de objeto (OLE) el `DAOTableDef` objetos (OLE). Además de su uso para examinar las propiedades del objeto, también puede usar `CDaoFieldInfo` para construir un parámetro de entrada para la creación de nuevos campos en una definición de tabla. La primera versión de `CreateField` es más fácil de usar, pero si desea un control más preciso, puede usar la segunda versión de `CreateField`, que toma un `CDaoFieldInfo` parámetro.

Si usa la versión de `CreateField` que toma un `CDaoFieldInfo` parámetro, debe cuidadosamente establecer cada uno de los siguientes miembros de la `CDaoFieldInfo` estructura:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Los miembros restantes de `CDaoFieldInfo` debe establecerse en **0**, FALSE o una cadena vacía, según corresponda para el miembro, o un `CDaoException` pueden producirse.

Para obtener información relacionada, vea el tema "Método CreateField" en la Ayuda de DAO.

##  <a name="createindex"></a>  CDaoTableDef::CreateIndex

Llame a esta función para agregar un índice a una tabla.

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parámetros

*indexinfo*<br/>
Una referencia a un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura.

### <a name="remarks"></a>Comentarios

Los índices especifican el orden de los registros que se obtiene acceso desde las tablas de base de datos y si se aceptan los registros duplicados. Los índices también proporcionan un acceso eficaz a los datos.

No es necesario que crear índices para tablas, pero en tablas grandes, no indizadas, el acceso a un registro determinado o crear un conjunto de registros puede tardar mucho tiempo. Por otro lado, crear demasiados índices ralentiza la actualización, anexar y eliminar operaciones como todos los índices se actualizan automáticamente. Tenga en cuenta estos factores al decidir qué índices se deben crear.

Los siguientes miembros de la `CDaoIndexInfo` se debe establecer la estructura:

- `m_strName` Debe proporcionarse un nombre.

- `m_pFieldInfos` Debe apuntar a una matriz de `CDaoIndexFieldInfo` estructuras.

- `m_nFields` Debe especificar el número de campos de la matriz de `CDaoFieldInfo` estructuras.

Los restantes miembros se omite si establecerá en FALSE. Además, el `m_lDistinctCount` miembro se omite durante la creación del índice.

##  <a name="deletefield"></a>  CDaoTableDef::DeleteField

Llame a esta función miembro para quitar un campo y que sea inaccesible.

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una expresión de cadena que es el nombre de un campo existente.

*nIndex*<br/>
El índice del campo en la colección de campos basada en cero de la tabla, para la búsqueda por índice.

### <a name="remarks"></a>Comentarios

Puede usar esta función miembro en un nuevo objeto que no se ha anexado a la base de datos o cuando [CanUpdate](#canupdate) devuelve cero.

Para obtener información relacionada, vea el tema "Método Delete" en la Ayuda de DAO.

##  <a name="deleteindex"></a>  CDaoTableDef::DeleteIndex

Llame a esta función miembro para eliminar un índice en una tabla subyacente.

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una expresión de cadena que es el nombre de un índice existente.

*nIndex*<br/>
El índice de matriz del objeto de índice en la colección de definiciones de tabla basada en cero de la base de datos, para la búsqueda por índice.

### <a name="remarks"></a>Comentarios

Puede usar esta función miembro en un nuevo objeto que no se ha anexado a la base de datos o cuando [CanUpdate](#canupdate) devuelve cero.

Para obtener información relacionada, vea el tema "Método Delete" en la Ayuda de DAO.

##  <a name="getattributes"></a>  CDaoTableDef::GetAttributes

Para un `CDaoTableDef` objeto, el valor devuelto especifica las características de la tabla representada por el `CDaoTableDef` de objetos y puede ser una suma de estas constantes:

```
long GetAttributes();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que indica una o varias características de un `CDaoTableDef` objeto.

### <a name="remarks"></a>Comentarios

|Constante|Descripción|
|--------------|-----------------|
|`dbAttachExclusive`|Para las bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que la tabla es una tabla asociada abierta para uso exclusivo.|
|`dbAttachSavePWD`|Para las bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que el Id. de usuario y la contraseña para la tabla asociada se guardan con la información de conexión.|
|`dbSystemObject`|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet.|
|`dbHiddenObject`|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet.|
|`dbAttachedTable`|Indica que la tabla es una tabla de una base de datos que no son ODBC, como una base de datos de Paradox asociada.|
|`dbAttachedODBC`|Indica que la tabla es una tabla de una base de datos ODBC, como Microsoft SQL Server asociada.|

Una tabla del sistema es una tabla creada por el motor de base de datos Microsoft Jet para incluir información interna distintos.

Una tabla oculta es una tabla creada para su uso temporal por el motor de base de datos Microsoft Jet.

Para obtener información relacionada, vea el tema "Atributos de propiedad" en la Ayuda de DAO.

##  <a name="getconnect"></a>  CDaoTableDef::GetConnect

Llame a esta función miembro para obtener la cadena de conexión para un origen de datos.

```
CString GetConnect();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` objeto que contiene el tipo de ruta de acceso y la base de datos para la tabla.

### <a name="remarks"></a>Comentarios

Para un `CDaoTableDef` objeto que representa una tabla asociada, la `CString` objeto consta de uno o dos partes (un especificador de tipo de base de datos y una ruta de acceso a la base de datos).

La ruta de acceso tal como se muestra en la tabla siguiente es la ruta de acceso completa del directorio que contiene los archivos de base de datos y debe ir precedido por el identificador "base de datos =". En algunos casos (como bases de datos con Microsoft Jet y Microsoft Excel), un nombre de archivo específico que se incluye en el argumento de ruta de acceso de la base de datos.

La tabla de [CDaoTableDef::SetConnect](#setconnect) muestra los tipos posibles de la base de datos y sus correspondientes especificadores de base de datos y las rutas de acceso:

Para las tablas de base de base de datos Microsoft Jet, el especificador es una cadena vacía ("").

Si se requiere una contraseña, pero no se proporciona, el controlador ODBC muestra un inicio de sesión cuadro de diálogo la primera vez que se tiene acceso a una tabla y de nuevo si la conexión se cierra y vuelve a abrir. Si tiene una tabla asociada la `dbAttachSavePWD` atributo, el símbolo del sistema de inicio de sesión no aparecerán cuando se vuelve a abrir la tabla.

Para obtener información relacionada, vea el tema "Propiedad conectarse" en la Ayuda de DAO.

##  <a name="getdatecreated"></a>  CDaoTableDef::GetDateCreated

Llame a esta función para determinar la fecha y hora de la tabla subyacente del `CDaoTableDef` se creó el objeto.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valor devuelto

Un valor que contiene la fecha y hora de la creación de la tabla subyacente del `CDaoTableDef` objeto.

### <a name="remarks"></a>Comentarios

La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la tabla base. En un entorno multiusuario, los usuarios deben obtener estos valores directamente desde el servidor de archivos para evitar las discrepancias; es decir, todos los clientes deben usar un origen de hora "estándar", quizás de un servidor.

Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.

##  <a name="getdatelastupdated"></a>  CDaoTableDef::GetDateLastUpdated

Llame a esta función para determinar la fecha y hora de la tabla subyacente del `CDaoTableDef` se actualizó por última vez el objeto.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valor devuelto

Un valor que contiene la fecha y hora de la tabla subyacente del `CDaoTableDef` se actualizó por última vez el objeto.

### <a name="remarks"></a>Comentarios

La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la tabla base. En un entorno multiusuario, los usuarios deben obtener estos valores directamente desde el servidor de archivos para evitar las discrepancias; es decir, todos los clientes deben usar un origen de hora "estándar", quizás de un servidor.

Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.

##  <a name="getfieldcount"></a>  CDaoTableDef::GetFieldCount

Llame a esta función miembro para recuperar el número de campos definidos en la tabla.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valor devuelto

El número de campos de la tabla.

### <a name="remarks"></a>Comentarios

Si su valor es 0, no hay ningún objeto en la colección.

Para obtener información relacionada, vea el tema "Propiedad Count" en la Ayuda de DAO.

##  <a name="getfieldinfo"></a>  CDaoTableDef::GetFieldInfo

Llame a esta función miembro para obtener diversos tipos de información sobre un campo definido en la definición de tabla.

```
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del objeto de campo en la colección de campos basada en cero de la tabla, para la búsqueda por índice.

*fieldinfo*<br/>
Una referencia a un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el campo que desea recuperar. Las opciones disponibles se muestran aquí, junto con lo que hacen que la función devolver:

- `AFX_DAO_PRIMARY_INFO` (Valor predeterminado) Nombre, tipo, tamaño, atributos. Use esta opción para obtener un rendimiento más rápido.

- `AFX_DAO_SECONDARY_INFO` La información principal, además de: Posición ordinal, es necesario, Permitir longitud cero, intercalación de orden, nombre de la externa, el campo de origen, tabla de origen

- `AFX_DAO_ALL_INFO` La información principal y secundaria, además de: Valor predeterminado de regla, el texto de validación de validación

*lpszName*<br/>
Un puntero al nombre del objeto de campo, para la búsqueda por nombre. El nombre es una cadena con hasta 64 caracteres que identifica inequívocamente el campo.

### <a name="remarks"></a>Comentarios

Una versión de la función le permite buscar un campo por su índice. La otra versión le permite buscar un campo por su nombre.

Para obtener una descripción de la información devuelta, consulte el [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información que aparece anteriormente en la descripción de *dwInfoOptions*. Cuando se solicita información en un nivel, obtendrá información de los niveles anteriores también.

Para obtener información relacionada, vea el tema "Atributos de propiedad" en la Ayuda de DAO.

##  <a name="getindexcount"></a>  CDaoTableDef::GetIndexCount

Llame a esta función miembro para obtener el número de índices de una tabla.

```
short GetIndexCount();
```

### <a name="return-value"></a>Valor devuelto

El número de índices de la tabla.

### <a name="remarks"></a>Comentarios

Si su valor es 0, no hay ningún índice en la colección.

Para obtener información relacionada, vea el tema "Propiedad Count" en la Ayuda de DAO.

##  <a name="getindexinfo"></a>  CDaoTableDef::GetIndexInfo

Llame a esta función miembro para obtener diversos tipos de información acerca de un índice definido en la definición de tabla.

```
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice numérico del objeto de índice en la colección de índices basada en cero de la tabla, para la búsqueda por su posición en la colección.

*indexinfo*<br/>
Una referencia a un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el índice para recuperar. Las opciones disponibles se muestran aquí, junto con lo que hacen que la función devolver:

- `AFX_DAO_PRIMARY_INFO` Campos de nombre, información de campo. Use esta opción para obtener un rendimiento más rápido.

- `AFX_DAO_SECONDARY_INFO` La información principal, además de: Principal, Unique, agrupado, omitir los valores NULL, requeridos, externos

- `AFX_DAO_ALL_INFO` La información principal y secundaria, además de: Recuento distinto

*lpszName*<br/>
Un puntero al nombre del objeto de índice, para la búsqueda por nombre.

### <a name="remarks"></a>Comentarios

Una versión de la función le permite buscar un índice por su posición en la colección. La otra versión le permite buscar un índice por nombre.

Para obtener una descripción de la información devuelta, consulte el [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información que aparece anteriormente en la descripción de *dwInfoOptions*. Cuando se solicita información en un nivel, obtendrá información de los niveles anteriores también.

Para obtener información relacionada, vea el tema "Atributos de propiedad" en la Ayuda de DAO.

##  <a name="getname"></a>  CDaoTableDef::GetName

Llame a esta función miembro para obtener el nombre definido por el usuario de la tabla subyacente.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

Un nombre definido por el usuario para una tabla.

### <a name="remarks"></a>Comentarios

Este nombre empieza por una letra y puede contener un máximo de 64 caracteres. Puede incluir números y caracteres de subrayado pero no puede incluir espacios o signos de puntuación.

Para obtener información relacionada, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

##  <a name="getrecordcount"></a>  CDaoTableDef::GetRecordCount

Llame a esta función miembro para averiguar cuántos registros se encuentran en un `CDaoTableDef` objeto.

```
long GetRecordCount();
```

### <a name="return-value"></a>Valor devuelto

El número de registros que se obtiene acceso en un objeto de definición de tabla.

### <a name="remarks"></a>Comentarios

Una llamada a `GetRecordCount` para un tipo de tabla `CDaoTableDef` objeto refleja el número aproximado de registros de la tabla y se verá afectado inmediatamente se agregan y eliminan registros de la tabla. Revierte las transacciones aparecerán como parte del número de registros hasta que llame a [CDaoWorkspace:: CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). Un `CDaoTableDef` objeto sin registros tiene un valor de propiedad de recuento de registros de 0. Al trabajar con tablas asociadas o bases de datos ODBC, `GetRecordCount` siempre devuelve -1.

Para obtener información relacionada, vea el tema "Propiedad RecordCount" en la Ayuda de DAO.

##  <a name="getsourcetablename"></a>  CDaoTableDef::GetSourceTableName

Llame a esta función miembro para recuperar el nombre de una tabla asociada en una base de datos de origen.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` objeto que especifica el nombre del origen de una tabla asociada, o una cadena vacía si una tabla de datos nativos.

### <a name="remarks"></a>Comentarios

Una tabla asociada es una tabla en otra base de datos vinculada a una base de datos Microsoft Jet. Los datos de tablas asociadas permanecen en la base de datos externo, donde se puede manipular por otras aplicaciones.

Para obtener información relacionada, vea el tema "SourceTableName Property" en la Ayuda de DAO.

##  <a name="getvalidationrule"></a>  CDaoTableDef::GetValidationRule

Llame a esta función miembro para recuperar la regla de validación para una definición de tabla.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` objeto que valida los datos de un campo cuando se cambia o se agregan a una tabla.

### <a name="remarks"></a>Comentarios

Las reglas de validación se usan en relación con las operaciones de actualización. Si una definición de tabla contiene una regla de validación, las actualizaciones de esa definición de tabla deben coincidir con los criterios predeterminados antes de que se modifican los datos. Si el cambio no coincide con los criterios, una excepción que contiene el valor de [GetValidationText](#getvalidationtext) se produce. Para un `CDaoTableDef` objeto esto `CString` es de solo lectura para una tabla asociada y lectura/escritura para una tabla base.

Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.

##  <a name="getvalidationtext"></a>  CDaoTableDef::GetValidationText

Llame a esta función para recuperar la cadena que se muestra cuando un usuario escribe datos que no coincide con la regla de validación.

```
CString GetValidationText();
```

### <a name="return-value"></a>Valor devuelto

Un `CString` objeto que especifica el texto que se muestra si el usuario escribe los datos que no coincide con la regla de validación.

### <a name="remarks"></a>Comentarios

Para un `CDaoTableDef` objeto esto `CString` es de solo lectura para una tabla asociada y lectura/escritura para una tabla base.

Para obtener información relacionada, vea el tema "Propiedad de texto de validación" en la Ayuda de DAO.

##  <a name="isopen"></a>  CDaoTableDef::IsOpen

Llame a esta función miembro para determinar si el `CDaoTableDef` objeto está abierto actualmente.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el `CDaoTableDef` objeto está abierta; de lo contrario, 0.

### <a name="remarks"></a>Comentarios

##  <a name="m_pdatabase"></a>  CDaoTableDef::m_pDatabase

Contiene un puntero a la [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto para esta tabla.

### <a name="remarks"></a>Comentarios

##  <a name="m_pdaotabledef"></a>  CDaoTableDef::m_pDAOTableDef

Contiene un puntero a la interfaz OLE para el objeto de definición de tabla DAO subyacente el `CDaoTableDef` objeto.

### <a name="remarks"></a>Comentarios

Use este puntero si necesita obtener acceso a la interfaz DAO directamente.

##  <a name="open"></a>  CDaoTableDef::Open

Llamada esta función miembro para abrir una definición de tabla previamente guardada en la base de datos del conjunto de definición de tabla.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una cadena que especifica un nombre de tabla.

### <a name="remarks"></a>Comentarios

##  <a name="refreshlink"></a>  CDaoTableDef::RefreshLink

Llame a esta función miembro para actualizar la información de conexión para una tabla asociada.

```
void RefreshLink();
```

### <a name="remarks"></a>Comentarios

Cambiar la información de conexión para una tabla asociada mediante una llamada a [SetConnect](#setconnect) en correspondiente `CDaoTableDef` objeto y, a continuación, usar el `RefreshLink` función miembro para actualizar la información. Cuando se llama a `RefreshLink`, no se cambian las propiedades de la tabla adjunto.

Para forzar la modificado información de conexión para que surta efecto, abrir todos los [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objetos en función de esta definición de tabla deben cerrarse.

Para obtener información relacionada, vea el tema "Método RefreshLink" en la Ayuda de DAO.

##  <a name="setattributes"></a>  CDaoTableDef::SetAttributes

Establece un valor que indica una o varias características de un `CDaoTableDef` objeto.

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parámetros

*lAttributes*<br/>
Características de la tabla representada por el `CDaoTableDef` de objetos y puede ser una suma de estas constantes:

|Constante|Descripción|
|--------------|-----------------|
|`dbAttachExclusive`|Para las bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que la tabla es una tabla asociada abierta para uso exclusivo.|
|`dbAttachSavePWD`|Para las bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que el Id. de usuario y la contraseña para la tabla asociada se guardan con la información de conexión.|
|`dbSystemObject`|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet.|
|`dbHiddenObject`|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet.|

### <a name="remarks"></a>Comentarios

Al establecer varios atributos, se pueden combinar sumando las constantes adecuadas mediante el operador OR bit a bit. Establecer `dbAttachExclusive` en una tabla no asociada produce una excepción. Combinación de los valores siguientes también generan una excepción:

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Para obtener información relacionada, vea el tema "Atributos de propiedad" en la Ayuda de DAO.

##  <a name="setconnect"></a>  CDaoTableDef::SetConnect

Para un `CDaoTableDef` objeto que representa una tabla asociada, el objeto de cadena consta de uno o dos partes (un especificador de tipo de base de datos y una ruta de acceso a la base de datos).

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parámetros

*lpszConnect*<br/>
Un puntero a una expresión de cadena que especifica parámetros adicionales que se va a pasar a ODBC o controladores ISAM instalables.

### <a name="remarks"></a>Comentarios

La ruta de acceso tal como se muestra en la tabla siguiente es la ruta de acceso completa del directorio que contiene los archivos de base de datos y debe ir precedido por el identificador "base de datos =". En algunos casos (como bases de datos con Microsoft Jet y Microsoft Excel), un nombre de archivo específico que se incluye en el argumento de ruta de acceso de la base de datos.

> [!NOTE]
>  No incluya espacios en blanco alrededor del signo igual en las instrucciones de la ruta de acceso del formulario "base de datos = unidad:\\\path". Esto provocará una excepción y el error de conexión.

La siguiente tabla muestra los tipos posibles de la base de datos y sus correspondientes especificadores de base de datos y las rutas de acceso:

|Tipo de base de datos|Especificador|Ruta de acceso|
|-------------------|---------------|----------|
|Base de datos mediante el motor de base de datos de Jet|"[ `database`];"|" `drive`:\\\ *ruta*\\\ *filename*. MDB"|
|dBASE III|"dBASE III;"|" `drive`:\\\ *ruta*"|
|dBASE IV|"dBASE IV;"|" `drive`:\\\ *ruta*"|
|5 de dBASE|"dBASE 5.0;"|" `drive`:\\\ *ruta*"|
|Paradox 3.x|"Paradox 3.x;"|" `drive`:\\\ *ruta*"|
|Paradox 4.x|"Paradox 4.x;"|" `drive`:\\\ *ruta*"|
|Paradox 5.x|"Paradox 5.x;"|" `drive`:\\\ *ruta*"|
|Excel 3.0|"Excel 3.0;"|" `drive`:\\\ *ruta*\\\ *filename*. XLS"|
|Excel 4.0|"Excel 4.0;"|" `drive`:\\\ *ruta*\\\ *filename*. XLS"|
|Excel 5.0 o Excel 95|"Excel 5.0;"|" `drive`:\\\ *ruta*\\\ *filename*. XLS"|
|Excel 97|"Excel 8.0;"|" `drive`:\\\ *ruta*\ *filename*. XLS"|
|Importar HTML|"Importar HTML;"|" `drive`:\\\ *ruta*\ *filename*"|
|Exportación de HTML|"Exportar HTML;"|" `drive`:\\\ *ruta*"|
|Texto|"Text";|"unidad:\\\path"|
|ODBC|"ODBC; Base de datos = `database`; UID = *usuario*; PWD = *contraseña*; DSN = *datasourcename;* LOGINTIMEOUT = *segundos;*" (Esto puede no ser una cadena de conexión completa para todos los servidores; es solo un ejemplo. Es muy importante no tienen espacios entre los parámetros.)|Ninguna|
|Exchange|"Exchange;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE={ 0 &#124; 1 };]<br /><br /> [PROFILE= *profile*;]<br /><br /> [PWD = *contraseña*;]<br /><br /> [BASE DE DATOS = `database`;] "|*"unidad*:\\\ *ruta*\\\ *filename*. MDB"|

> [!NOTE]
>  Btrieve ya no se admite a partir de DAO 3.5.

Debe usar una doble barra diagonal inversa (\\\\) en las cadenas de conexión. Si ha modificado las propiedades de una conexión existente con `SetConnect`, debe llamar posteriormente a [RefreshLink](#refreshlink). Si se están inicializando las propiedades de conexión mediante `SetConnect`, necesita no llamada `RefreshLink`, pero en primer lugar si decide hacerlo, anexe la definición de tabla.

Si se requiere una contraseña, pero no se proporciona, el controlador ODBC muestra un inicio de sesión cuadro de diálogo la primera vez que se tiene acceso a una tabla y de nuevo si la conexión se cierra y vuelve a abrir.

Puede establecer la cadena de conexión para un `CDaoTableDef` objeto para proporcionar un argumento de origen a la `Create` función miembro. Puede comprobar la configuración para determinar el tipo, ruta de acceso, Id. de usuario, contraseña o el origen de datos de la base de datos. Para obtener más información, consulte la documentación para el controlador específico.

Para obtener información relacionada, vea el tema "Propiedad conectarse" en la Ayuda de DAO.

##  <a name="setname"></a>  CDaoTableDef::SetName

Llame a esta función miembro para establecer un nombre definido por el usuario para una tabla.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una expresión de cadena que especifica un nombre para una tabla.

### <a name="remarks"></a>Comentarios

El nombre debe empezar por una letra y puede contener un máximo de 64 caracteres. Puede incluir números y caracteres de subrayado pero no puede incluir espacios o signos de puntuación.

Para obtener información relacionada, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

##  <a name="setsourcetablename"></a>  CDaoTableDef::SetSourceTableName

Llame a esta función miembro para especificar el nombre de una tabla asociada o el nombre de la tabla base en el que el `CDaoTableDef` se basa el objeto, tal como existe en el origen de los datos.

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parámetros

*lpszSrcTableName*<br/>
Un puntero a una expresión de cadena que especifica un nombre de tabla en la base de datos externo. Para una tabla base, el valor es una cadena vacía ("").

### <a name="remarks"></a>Comentarios

A continuación, debe llamar a [RefreshLink](#refreshlink). Valor de esta propiedad está vacío para una tabla base y la lectura y escritura para una tabla asociada o un objeto que no se anexa a una colección.

Para obtener información relacionada, vea el tema "SourceTableName Property" en la Ayuda de DAO.

##  <a name="setvalidationrule"></a>  CDaoTableDef::SetValidationRule

Llame a esta función miembro para establecer una regla de validación para una definición de tabla.

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parámetros

*lpszValidationRule*<br/>
Un puntero a una expresión de cadena que se valida una operación.

### <a name="remarks"></a>Comentarios

Las reglas de validación se usan en relación con las operaciones de actualización. Si una definición de tabla contiene una regla de validación, las actualizaciones de esa definición de tabla deben coincidir con los criterios predeterminados antes de que se modifican los datos. Si el cambio no coincide con los criterios, una excepción que contiene el texto de [GetValidationText](#getvalidationtext) se muestra.

Validación solo se admite para las bases de datos que utilizan el motor de base de datos Microsoft Jet. La expresión no puede hacer referencia a las funciones definidas por el usuario, funciones de agregado de dominio, las funciones de agregado de SQL o consultas. Una regla de validación para una `CDaoTableDef` objeto puede hacer referencia a varios campos de ese objeto.

Por ejemplo, para los campos denominados *hire_date* y *termination_date*, podría ser una regla de validación:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.

##  <a name="setvalidationtext"></a>  CDaoTableDef::SetValidationText

Llame a esta función miembro para establecer el texto de la excepción de una regla de validación para una `CDaoTableDef` objeto con una tabla base subyacente compatible con el motor de base de datos Microsoft Jet.

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parámetros

*lpszValidationText*<br/>
Un puntero a una expresión de cadena que especifica el texto mostrado si escribe datos no es válido.

### <a name="remarks"></a>Comentarios

No se puede establecer el texto de validación de una tabla asociada.

Para obtener información relacionada, vea el tema "Propiedad de texto de validación" en la Ayuda de DAO.

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)
