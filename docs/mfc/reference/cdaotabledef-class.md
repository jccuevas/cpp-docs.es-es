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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424516"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef (clase)

Representa la definición almacenada de una tabla base o una tabla asociada.

## <a name="syntax"></a>Sintaxis

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoTableDef:: CDaoTableDef](#cdaotabledef)|Construye un objeto `CDaoTableDef`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoTableDef:: Append](#append)|Agrega una nueva tabla a la base de datos.|
|[CDaoTableDef:: CanUpdate](#canupdate)|Devuelve un valor distinto de cero si la tabla se puede actualizar (puede modificar la definición de los campos o las propiedades de la tabla).|
|[CDaoTableDef:: Close](#close)|Cierra un TableDef abierto.|
|[CDaoTableDef:: Create](#create)|Crea una tabla que se puede Agregar a la base de datos mediante [Append](#append).|
|[CDaoTableDef:: CreateField](#createfield)|Se llama para crear un campo para una tabla.|
|[CDaoTableDef:: CreateIndex](#createindex)|Se llama para crear un índice para una tabla.|
|[CDaoTableDef::D eleteField](#deletefield)|Se llama para eliminar un campo de una tabla.|
|[CDaoTableDef::D eleteIndex](#deleteindex)|Se llama para eliminar un índice de una tabla.|
|[CDaoTableDef:: GetAttributes](#getattributes)|Devuelve un valor que indica una o más características de un objeto `CDaoTableDef`.|
|[CDaoTableDef:: GetConnect](#getconnect)|Devuelve un valor que proporciona información sobre el origen de una tabla.|
|[CDaoTableDef:: GetDateCreated](#getdatecreated)|Devuelve la fecha y hora en que se creó la tabla base subyacente a un objeto `CDaoTableDef`.|
|[CDaoTableDef:: GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha y hora del cambio más reciente realizado en el diseño de la tabla base.|
|[CDaoTableDef:: GetFieldCount](#getfieldcount)|Devuelve un valor que representa el número de campos de la tabla.|
|[CDaoTableDef:: GetFieldInfo](#getfieldinfo)|Devuelve tipos específicos de información sobre los campos de la tabla.|
|[CDaoTableDef:: GetIndexCount](#getindexcount)|Devuelve el número de índices de la tabla.|
|[CDaoTableDef:: GetIndexInfo](#getindexinfo)|Devuelve tipos específicos de información sobre los índices de la tabla.|
|[CDaoTableDef:: GetName](#getname)|Devuelve el nombre definido por el usuario de la tabla.|
|[CDaoTableDef:: GetRecordCount](#getrecordcount)|Devuelve el número de registros de la tabla.|
|[CDaoTableDef:: GetSourceTableName](#getsourcetablename)|Devuelve un valor que especifica el nombre de la tabla adjunta en la base de datos de origen.|
|[CDaoTableDef:: GetValidationRule](#getvalidationrule)|Devuelve un valor que valida los datos de un campo a medida que se cambian o se agregan a una tabla.|
|[CDaoTableDef:: GetValidationText](#getvalidationtext)|Devuelve un valor que especifica el texto del mensaje que la aplicación muestra si el valor de un objeto de campo no satisface la regla de validación especificada.|
|[CDaoTableDef:: IsOpen](#isopen)|Devuelve un valor distinto de cero si la tabla está abierta.|
|[CDaoTableDef:: Open](#open)|Abre un TableDef existente almacenado en la colección TableDef's de la base de datos.|
|[CDaoTableDef:: RefreshLink](#refreshlink)|Actualiza la información de conexión para una tabla adjunta.|
|[CDaoTableDef:: SetAttributes](#setattributes)|Establece un valor que indica una o más características de un objeto `CDaoTableDef`.|
|[CDaoTableDef:: SetConnect](#setconnect)|Establece un valor que proporciona información sobre el origen de una tabla.|
|[CDaoTableDef:: SetName](#setname)|Establece el nombre de la tabla.|
|[CDaoTableDef:: SetSourceTableName](#setsourcetablename)|Establece un valor que especifica el nombre de una tabla adjunta en la base de datos de origen.|
|[CDaoTableDef:: SetValidationRule](#setvalidationrule)|Establece un valor que valida los datos de un campo a medida que se cambian o se agregan a una tabla.|
|[CDaoTableDef:: SetValidationText](#setvalidationtext)|Establece un valor que especifica el texto del mensaje que la aplicación muestra si el valor de un objeto de campo no satisface la regla de validación especificada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoTableDef:: m_pDAOTableDef](#m_pdaotabledef)|Puntero a la interfaz de DAO subyacente del objeto TableDef.|
|[CDaoTableDef:: m_pDatabase](#m_pdatabase)|Base de datos de origen de esta tabla.|

## <a name="remarks"></a>Observaciones

Cada objeto de base de datos DAO mantiene una colección, denominada TableDefs, que contiene todos los objetos DAO TableDef guardados.

Puede manipular una definición de tabla mediante un objeto `CDaoTableDef`. Por ejemplo, puede:

- Examinar la estructura de campo y de índice de cualquier tabla local, adjunta o externa de una base de datos.

- Llame a las funciones miembro `SetConnect` y `SetSourceTableName` para las tablas adjuntas y utilice la función miembro `RefreshLink` para actualizar las conexiones a las tablas asociadas.

- Llame a la función miembro `CanUpdate` para determinar si puede editar las definiciones de campo en la tabla.

- Obtiene o establece las condiciones de validación mediante el `GetValidationRule` y `SetValidationRule`, y las funciones miembro `GetValidationText` y `SetValidationText`.

- Utilice la función miembro `Open` para crear un objeto `CDaoRecordset` de tipo tabla, Dynaset o Snapshot.

    > [!NOTE]
    >  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Conectividad abierta de bases de datos (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede obtener acceso a los orígenes de datos ODBC con las clases DAO; las clases DAO suelen ofrecer funcionalidades superiores porque son específicas del motor de base de datos de Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Para utilizar objetos tabledef para trabajar con una tabla existente o crear una nueva tabla

1. En todos los casos, primero construya un objeto `CDaoTableDef`, proporcionando un puntero a un objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) al que pertenece la tabla.

1. A continuación, haga lo siguiente, en función de lo que desee:

   - Para usar una tabla guardada existente, llame a la función miembro [Open](#open) del objeto TableDef y proporcione el nombre de la tabla guardada.

   - Para crear una nueva tabla, llame a la función miembro [Create](#create) del objeto TableDef y proporcione el nombre de la tabla. Llame a [CreateField](#createfield) y [CreateIndex](#createindex) para agregar campos e índices a la tabla.

   - Llame a [Append](#append) para guardar la tabla; para ello, agréguelo a la colección TableDefs de la base de datos. `Create` pone el objeto TableDef en un estado abierto, por lo que después de llamar a `Create` no se llama a `Open`.

        > [!TIP]
        >  La manera más sencilla de crear tablas guardadas es crearlas y almacenarlas en la base de datos mediante Microsoft Access. Después, puede abrirlos y usarlos en el código MFC.

Para usar el objeto TableDef que ha abierto o creado, cree y abra un objeto `CDaoRecordset`, especificando el nombre de TableDef con un valor `dbOpenTable` en el parámetro *nOpenType* .

Para usar un objeto TableDef para crear un objeto `CDaoRecordset`, normalmente se crea o se abre un objeto TableDef como se describió anteriormente y, a continuación, se genera un objeto de conjunto de registros, pasando un puntero al objeto TableDef cuando se llama a [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). El TableDef que pase debe estar en un estado abierto. Para obtener más información, vea la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Cuando termine de usar un objeto TableDef, llame a la función miembro [Close](../../mfc/reference/cdaorecordset-class.md#close) ; a continuación, destruya el objeto TableDef.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

##  <a name="append"></a>CDaoTableDef:: Append

Llame a esta función miembro después de llamar a [Create](#create) para crear un nuevo objeto TableDef para guardar TableDef en la base de datos.

```
virtual void Append();
```

### <a name="remarks"></a>Observaciones

La función anexa el objeto a la colección TableDefs de la base de datos. Puede usar TableDef como un objeto temporal mientras lo define sin anexarlo, pero si desea guardarlo y usarlo, debe llamar a `Append`.

> [!NOTE]
>  Si intenta anexar una definición de tipo sin nombre (que contiene una cadena nula o vacía), MFC produce una excepción.

Para obtener información relacionada, vea el tema sobre el método Append en la ayuda de DAO.

##  <a name="canupdate"></a>CDaoTableDef:: CanUpdate

Llame a esta función miembro para determinar si se puede cambiar la definición de la tabla subyacente a un objeto `CDaoTableDef`.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se puede modificar la estructura de la tabla (esquema) (agregar o eliminar campos e índices), de lo contrario 0.

### <a name="remarks"></a>Observaciones

De forma predeterminada, una tabla recién creada subyacente a un objeto de `CDaoTableDef` se puede actualizar y no se puede actualizar una tabla adjunta subyacente a un objeto `CDaoTableDef`. Un objeto `CDaoTableDef` puede ser actualizable, incluso si el conjunto de registros resultante no es actualizable.

Para obtener información relacionada, vea el tema "propiedad actualizable" en la ayuda de DAO.

##  <a name="cdaotabledef"></a>CDaoTableDef:: CDaoTableDef

Construye un objeto `CDaoTableDef`.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parámetros

*pDatabase*<br/>
Un puntero a un objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .

### <a name="remarks"></a>Observaciones

Después de construir el objeto, debe llamar a la función miembro [Create](#create) o [Open](#open) . Cuando termine con el objeto, debe llamar a la función miembro [Close](#close) y destruir el objeto `CDaoTableDef`.

##  <a name="close"></a>CDaoTableDef:: Close

Llame a esta función miembro para cerrar y liberar el objeto TableDef.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Normalmente después de llamar a `Close`, se elimina el objeto TableDef si se asignó con **New**.

Puede llamar a [Open](#open) de nuevo después de llamar a `Close`. Esto le permite volver a usar el objeto TableDef.

Para obtener información relacionada, vea el tema sobre el método Close en la ayuda de DAO.

##  <a name="create"></a>CDaoTableDef:: Create

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
Puntero a una cadena que contiene el nombre de la tabla.

*lAttributes*<br/>
Un valor que corresponde a las características de la tabla representada por el objeto TableDef. Puede usar la operación OR bit a bit para combinar cualquiera de las constantes siguientes:

|Constante|Descripción|
|--------------|-----------------|
|`dbAttachExclusive`|En el caso de las bases de datos que usan el motor de base de datos de Microsoft Jet, indica que la tabla es una tabla adjunta abierta para uso exclusivo.|
|`dbAttachSavePWD`|En el caso de las bases de datos que usan el motor de base de datos de Microsoft Jet, indica que el ID. de usuario y la contraseña de la tabla adjunta se guardan con la información de conexión.|
|`dbSystemObject`|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos de Microsoft Jet.|
|`dbHiddenObject`|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos de Microsoft Jet.|

*lpszSrcTable*<br/>
Puntero a una cadena que contiene el nombre de la tabla de origen. De forma predeterminada, este valor se inicializa como NULL.

*lpszConnect*<br/>
Puntero a una cadena que contiene la cadena de conexión predeterminada. De forma predeterminada, este valor se inicializa como NULL.

### <a name="remarks"></a>Observaciones

Una vez que haya llamado a TableDef, puede llamar a [Append](#append) para guardar el TableDef en la colección TableDefs de la base de datos. Después de llamar a `Append`, el objeto TableDef está en un estado abierto y puede usarlo para crear un objeto [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .

Para obtener información relacionada, vea el tema sobre el método CreateTableDef en la ayuda de DAO.

##  <a name="createfield"></a>CDaoTableDef:: CreateField

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
Valor que indica el tipo de datos del campo. El valor puede ser uno de estos valores:

|Tipo|Tamaño (bytes)|Descripción|
|----------|--------------------|-----------------|
|`dbBoolean`|1 byte|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|Moneda ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|FLOAT|
|`dbDouble`|8|double|
|`dbDate`|8|Fecha y hora ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texto ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (objeto OLE), [CLongBinary](../../mfc/reference/clongbinary-class.md) o [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Memorando ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Valor que indica el tamaño máximo, en bytes, de un campo que contiene texto o el tamaño fijo de un campo que contiene valores de texto o numéricos. El parámetro *Lsize* se omite para todos los campos de texto excepto.

*lAttributes*<br/>
Un valor que corresponde a las características del campo y que se puede combinar mediante una operación OR bit a bit.

|Constante|Descripción|
|--------------|-----------------|
|`dbFixedField`|El tamaño del campo es fijo (valor predeterminado para los campos numéricos).|
|`dbVariableField`|El tamaño del campo es variable (solo campos de texto).|
|`dbAutoIncrField`|El valor del campo para los nuevos registros se incrementa automáticamente a un entero largo único que no se puede cambiar. Solo se admite para las tablas de base de datos de Microsoft Jet.|
|`dbUpdatableField`|Se puede cambiar el valor del campo.|
|`dbDescending`|El campo se ordena en orden descendente (Z-A o 100-0) (se aplica solo a un objeto de campo de una colección de campos de un objeto de índice). Si omite esta constante, el campo se ordena en orden ascendente (A-Z o 0-100) (valor predeterminado).|

*FieldInfo*<br/>
Referencia a una estructura [cdaofieldinfo (](../../mfc/reference/cdaofieldinfo-structure.md) .

### <a name="remarks"></a>Observaciones

Se crea un objeto `DAOField` (OLE) y se anexa a la colección Fields del objeto `DAOTableDef` (OLE). Además de su uso para examinar las propiedades de objeto, también puede utilizar `CDaoFieldInfo` para construir un parámetro de entrada para crear nuevos campos en una definición de objetos. La primera versión de `CreateField` es más fácil de usar, pero si desea un control más preciso, puede usar la segunda versión de `CreateField`, que toma un parámetro `CDaoFieldInfo`.

Si usa la versión de `CreateField` que toma un parámetro `CDaoFieldInfo`, debe establecer cuidadosamente cada uno de los siguientes miembros de la estructura `CDaoFieldInfo`:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Los miembros restantes de `CDaoFieldInfo` deben establecerse en **0**, false o en una cadena vacía, según sea necesario para el miembro, o puede producirse un `CDaoException`.

Para obtener información relacionada, vea el tema "método CreateField" en la ayuda de DAO.

##  <a name="createindex"></a>CDaoTableDef:: CreateIndex

Llame a esta función para agregar un índice a una tabla.

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parámetros

*indexinfo*<br/>
Referencia a una estructura [cdaoindexinfo (](../../mfc/reference/cdaoindexinfo-structure.md) .

### <a name="remarks"></a>Observaciones

Los índices especifican el orden de los registros a los que se obtiene acceso desde las tablas de base de datos y si se aceptan o no registros duplicados. Los índices también proporcionan un acceso eficaz a los datos.

No es necesario crear índices para las tablas, pero en las tablas grandes y sin indexar, el acceso a un registro específico o la creación de un conjunto de registros pueden tardar mucho tiempo. Por otro lado, la creación de demasiados índices reduce la velocidad de las operaciones de actualización, anexión y eliminación, ya que todos los índices se actualizan automáticamente. Tenga en cuenta estos factores a medida que decida qué índices crear.

Se deben establecer los siguientes miembros de la estructura `CDaoIndexInfo`:

- `m_strName` se debe proporcionar un nombre.

- `m_pFieldInfos` debe apuntar a una matriz de estructuras de `CDaoIndexFieldInfo`.

- `m_nFields` debe especificar el número de campos de la matriz de estructuras de `CDaoFieldInfo`.

Los miembros restantes se omitirán si se establece en FALSE. Además, el miembro de `m_lDistinctCount` se omite durante la creación del índice.

##  <a name="deletefield"></a>CDaoTableDef::D eleteField

Llame a esta función miembro para quitar un campo y hacer que sea inaccesible.

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una expresión de cadena que es el nombre de un campo existente.

*nIndex*<br/>
Índice del campo de la colección de campos de base cero de la tabla, para la búsqueda por índice.

### <a name="remarks"></a>Observaciones

Puede utilizar esta función miembro en un nuevo objeto que no se haya anexado a la base de datos o cuando [CanUpdate](#canupdate) devuelva un valor distinto de cero.

Para obtener información relacionada, vea el tema "eliminar método" en la ayuda de DAO.

##  <a name="deleteindex"></a>CDaoTableDef::D eleteIndex

Llame a esta función miembro para eliminar un índice de una tabla subyacente.

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una expresión de cadena que es el nombre de un índice existente.

*nIndex*<br/>
Índice de matriz del objeto index de la colección TableDefs de base cero de la base de datos, para la búsqueda por índice.

### <a name="remarks"></a>Observaciones

Puede utilizar esta función miembro en un nuevo objeto que no se haya anexado a la base de datos o cuando [CanUpdate](#canupdate) devuelva un valor distinto de cero.

Para obtener información relacionada, vea el tema "eliminar método" en la ayuda de DAO.

##  <a name="getattributes"></a>CDaoTableDef:: GetAttributes

Para un objeto `CDaoTableDef`, el valor devuelto especifica las características de la tabla representada por el objeto `CDaoTableDef` y puede ser una suma de estas constantes:

```
long GetAttributes();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que indica una o más características de un objeto `CDaoTableDef`.

### <a name="remarks"></a>Observaciones

|Constante|Descripción|
|--------------|-----------------|
|`dbAttachExclusive`|En el caso de las bases de datos que usan el motor de base de datos de Microsoft Jet, indica que la tabla es una tabla adjunta abierta para uso exclusivo.|
|`dbAttachSavePWD`|En el caso de las bases de datos que usan el motor de base de datos de Microsoft Jet, indica que el ID. de usuario y la contraseña de la tabla adjunta se guardan con la información de conexión.|
|`dbSystemObject`|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos de Microsoft Jet.|
|`dbHiddenObject`|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos de Microsoft Jet.|
|`dbAttachedTable`|Indica que la tabla es una tabla adjunta de una base de datos que no es de ODBC, como una base de datos de Paradox.|
|`dbAttachedODBC`|Indica que la tabla es una tabla adjunta de una base de datos ODBC, como Microsoft SQL Server.|

Una tabla del sistema es una tabla creada por el motor de base de datos de Microsoft Jet para que contenga diversa información interna.

Una tabla oculta es una tabla creada para su uso temporal por el motor de base de datos de Microsoft Jet.

Para obtener información relacionada, vea el tema "propiedad Attributes" en la ayuda de DAO.

##  <a name="getconnect"></a>CDaoTableDef:: GetConnect

Llame a esta función miembro para obtener la cadena de conexión de un origen de datos.

```
CString GetConnect();
```

### <a name="return-value"></a>Valor devuelto

`CString` objeto que contiene la ruta de acceso y el tipo de base de datos de la tabla.

### <a name="remarks"></a>Observaciones

Para un objeto `CDaoTableDef` que representa una tabla adjunta, el objeto `CString` está formado por una o dos partes (un especificador de tipo de base de datos y una ruta de acceso a la base de datos).

La ruta de acceso tal como se muestra en la tabla siguiente es la ruta de acceso completa del directorio que contiene los archivos de base de datos y debe ir precedida del identificador "DATABASE =". En algunos casos (al igual que con las bases de datos de Microsoft Jet y Microsoft Excel), se incluye un nombre de archivo específico en el argumento de ruta de acceso de la base de datos.

La tabla de [CDaoTableDef:: SetConnect](#setconnect) muestra los tipos de base de datos posibles y sus correspondientes especificadores de base de datos y rutas de acceso:

En el caso de las tablas base de base de datos de Microsoft Jet, el especificador es una cadena vacía ("").

Si se requiere una contraseña, pero no se proporciona, el controlador ODBC muestra un cuadro de diálogo de inicio de sesión la primera vez que se tiene acceso a una tabla y de nuevo si la conexión se cierra y se vuelve a abrir. Si una tabla adjunta tiene el atributo `dbAttachSavePWD`, no aparecerá el mensaje de inicio de sesión cuando se vuelva a abrir la tabla.

Para obtener información relacionada, vea el tema "propiedad de conexión" en la ayuda de DAO.

##  <a name="getdatecreated"></a>CDaoTableDef:: GetDateCreated

Llame a esta función para determinar la fecha y hora en que se creó la tabla subyacente del objeto `CDaoTableDef`.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valor devuelto

Valor que contiene la fecha y hora de creación de la tabla subyacente al objeto `CDaoTableDef`.

### <a name="remarks"></a>Observaciones

La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la tabla base. En un entorno multiusuario, los usuarios deben obtener esta configuración directamente desde el servidor de archivos para evitar discrepancias. es decir, todos los clientes deben usar un origen de hora "estándar", quizás de un servidor.

Para obtener información relacionada, vea el tema "DateCreated, propiedades de LastUpdated" en la ayuda de DAO.

##  <a name="getdatelastupdated"></a>CDaoTableDef:: GetDateLastUpdated

Llame a esta función para determinar la fecha y hora en que se actualizó por última vez la tabla subyacente del objeto `CDaoTableDef`.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valor devuelto

Valor que contiene la fecha y hora en que se actualizó por última vez la tabla subyacente al objeto de `CDaoTableDef`.

### <a name="remarks"></a>Observaciones

La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la tabla base. En un entorno multiusuario, los usuarios deben obtener esta configuración directamente desde el servidor de archivos para evitar discrepancias. es decir, todos los clientes deben usar un origen de hora "estándar", quizás de un servidor.

Para obtener información relacionada, vea el tema "DateCreated, propiedades de LastUpdated" en la ayuda de DAO.

##  <a name="getfieldcount"></a>CDaoTableDef:: GetFieldCount

Llame a esta función miembro para recuperar el número de campos definidos en la tabla.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valor devuelto

Número de campos de la tabla.

### <a name="remarks"></a>Observaciones

Si su valor es 0, no hay ningún objeto en la colección.

Para obtener información relacionada, vea el tema "propiedad Count" en la ayuda de DAO.

##  <a name="getfieldinfo"></a>CDaoTableDef:: GetFieldInfo

Llame a esta función miembro para obtener varios tipos de información sobre un campo definido en la definición de tipo.

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
Índice del objeto de campo en la colección de campos de base cero de la tabla, para la búsqueda por índice.

*FieldInfo*<br/>
Referencia a una estructura [cdaofieldinfo (](../../mfc/reference/cdaofieldinfo-structure.md) .

*dwInfoOptions*<br/>
Opciones que especifican la información sobre el campo que se va a recuperar. Aquí se enumeran las opciones disponibles junto con lo que hacen que la función devuelva:

- `AFX_DAO_PRIMARY_INFO` (valor predeterminado) nombre, tipo, tamaño, atributos. Use esta opción para obtener un rendimiento más rápido.

- `AFX_DAO_SECONDARY_INFO` información principal, más: posición ordinal, requerida, Permitir longitud cero, orden de intercalación, nombre externo, campo de origen, tabla de origen

- `AFX_DAO_ALL_INFO` información principal y secundaria, más: regla de validación, texto de validación, valor predeterminado

*lpszName*<br/>
Puntero al nombre del objeto de campo, para buscar por nombre. El nombre es una cadena con un máximo de 64 caracteres que nombra el campo de forma única.

### <a name="remarks"></a>Observaciones

Una versión de la función permite buscar un campo por índice. La otra versión permite buscar un campo por nombre.

Para obtener una descripción de la información devuelta, consulte la estructura [cdaofieldinfo (](../../mfc/reference/cdaofieldinfo-structure.md) . Esta estructura tiene miembros que corresponden a los elementos de la información enumerados anteriormente en la descripción de *dwInfoOptions*. Cuando se solicita información en un nivel, también se obtiene información sobre cualquier nivel anterior.

Para obtener información relacionada, vea el tema "propiedad Attributes" en la ayuda de DAO.

##  <a name="getindexcount"></a>CDaoTableDef:: GetIndexCount

Llame a esta función miembro para obtener el número de índices de una tabla.

```
short GetIndexCount();
```

### <a name="return-value"></a>Valor devuelto

Número de índices de la tabla.

### <a name="remarks"></a>Observaciones

Si su valor es 0, no hay ningún índice en la colección.

Para obtener información relacionada, vea el tema "propiedad Count" en la ayuda de DAO.

##  <a name="getindexinfo"></a>CDaoTableDef:: GetIndexInfo

Llame a esta función miembro para obtener varios tipos de información sobre un índice definido en la definición de tipo.

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
Índice numérico del objeto index de la colección de índices de base cero de la tabla, para la búsqueda por su posición en la colección.

*indexinfo*<br/>
Referencia a una estructura [cdaoindexinfo (](../../mfc/reference/cdaoindexinfo-structure.md) .

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el índice se va a recuperar. Aquí se enumeran las opciones disponibles junto con lo que hacen que la función devuelva:

- Nombre de `AFX_DAO_PRIMARY_INFO`, información de campo, campos. Use esta opción para obtener un rendimiento más rápido.

- `AFX_DAO_SECONDARY_INFO` información principal, además de: principal, único, agrupado, omitir valores NULL, requerido, externo

- `AFX_DAO_ALL_INFO` información principal y secundaria, más: recuento distintivo

*lpszName*<br/>
Puntero al nombre del objeto de índice, para la búsqueda por nombre.

### <a name="remarks"></a>Observaciones

Una versión de la función permite buscar un índice por su posición en la colección. La otra versión permite buscar un índice por nombre.

Para obtener una descripción de la información devuelta, consulte la estructura [cdaoindexinfo (](../../mfc/reference/cdaoindexinfo-structure.md) . Esta estructura tiene miembros que corresponden a los elementos de la información enumerados anteriormente en la descripción de *dwInfoOptions*. Cuando se solicita información en un nivel, también se obtiene información sobre cualquier nivel anterior.

Para obtener información relacionada, vea el tema "propiedad Attributes" en la ayuda de DAO.

##  <a name="getname"></a>CDaoTableDef:: GetName

Llame a esta función miembro para obtener el nombre definido por el usuario de la tabla subyacente.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

Nombre definido por el usuario para una tabla.

### <a name="remarks"></a>Observaciones

Este nombre empieza por una letra y puede contener un máximo de 64 caracteres. Puede incluir números y caracteres de subrayado, pero no puede incluir signos de puntuación ni espacios.

Para obtener información relacionada, vea el tema "propiedad de nombre" en la ayuda de DAO.

##  <a name="getrecordcount"></a>CDaoTableDef:: GetRecordCount

Llame a esta función miembro para averiguar cuántos registros hay en un objeto `CDaoTableDef`.

```
long GetRecordCount();
```

### <a name="return-value"></a>Valor devuelto

Número de registros a los que se tiene acceso en un objeto TableDef.

### <a name="remarks"></a>Observaciones

La llamada a `GetRecordCount` para un objeto de `CDaoTableDef` de tipo de tabla refleja el número aproximado de registros de la tabla y se ve afectado inmediatamente a medida que se agregan y eliminan registros de tabla. Las transacciones revertidas aparecerán como parte del número de registros hasta que se llame a [CDaoWorkSpace:: CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). Un objeto `CDaoTableDef` sin registros tiene un valor de la propiedad recuento de registros de 0. Al trabajar con tablas o bases de datos ODBC adjuntas, `GetRecordCount` siempre devuelve-1.

Para obtener información relacionada, vea el tema "propiedad RecordCount" en la ayuda de DAO.

##  <a name="getsourcetablename"></a>CDaoTableDef:: GetSourceTableName

Llame a esta función miembro para recuperar el nombre de una tabla adjunta en una base de datos de origen.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que especifica el nombre de origen de una tabla adjunta, o una cadena vacía si se trata de una tabla de datos nativa.

### <a name="remarks"></a>Observaciones

Una tabla adjunta es una tabla de otra base de datos vinculada a una base de datos de Microsoft Jet. Los datos de las tablas asociadas permanecen en la base de datos externa, donde pueden ser manipulados por otras aplicaciones.

Para obtener información relacionada, vea el tema "propiedad SourceTableName" en la ayuda de DAO.

##  <a name="getvalidationrule"></a>CDaoTableDef:: GetValidationRule

Llame a esta función miembro para recuperar la regla de validación para una definición de usuario.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que valida los datos de un campo a medida que se cambian o se agregan a una tabla.

### <a name="remarks"></a>Observaciones

Las reglas de validación se usan en relación con las operaciones de actualización. Si un TableDef contiene una regla de validación, las actualizaciones de ese TableDef deben coincidir con los criterios predeterminados antes de que se cambien los datos. Si el cambio no coincide con los criterios, se produce una excepción que contiene el valor de [GetValidationText](#getvalidationtext) . Para un objeto `CDaoTableDef`, este `CString` es de solo lectura para una tabla adjunta y de lectura y escritura para una tabla base.

Para obtener información relacionada, vea el tema "propiedad ValidationRule" en la ayuda de DAO.

##  <a name="getvalidationtext"></a>CDaoTableDef:: GetValidationText

Llame a esta función para recuperar la cadena que se va a mostrar cuando un usuario escriba datos que no coincidan con la regla de validación.

```
CString GetValidationText();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que especifica el texto que se muestra si el usuario escribe datos que no coinciden con la regla de validación.

### <a name="remarks"></a>Observaciones

Para un objeto `CDaoTableDef`, este `CString` es de solo lectura para una tabla adjunta y de lectura y escritura para una tabla base.

Para obtener información relacionada, vea el tema "propiedad ValidationText" en la ayuda de DAO.

##  <a name="isopen"></a>CDaoTableDef:: IsOpen

Llame a esta función miembro para determinar si el objeto `CDaoTableDef` está abierto actualmente.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de `CDaoTableDef` está abierto; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

##  <a name="m_pdatabase"></a>CDaoTableDef:: m_pDatabase

Contiene un puntero al objeto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) de esta tabla.

### <a name="remarks"></a>Observaciones

##  <a name="m_pdaotabledef"></a>CDaoTableDef:: m_pDAOTableDef

Contiene un puntero a la interfaz OLE para el objeto DAO TableDef subyacente al objeto `CDaoTableDef`.

### <a name="remarks"></a>Observaciones

Utilice este puntero si necesita tener acceso a la interfaz de DAO directamente.

##  <a name="open"></a>CDaoTableDef:: Open

Llame a esta función miembro para abrir un TableDef guardado previamente en la colección TableDef's de la base de datos.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una cadena que especifica un nombre de tabla.

### <a name="remarks"></a>Observaciones

##  <a name="refreshlink"></a>CDaoTableDef:: RefreshLink

Llame a esta función miembro para actualizar la información de conexión de una tabla adjunta.

```
void RefreshLink();
```

### <a name="remarks"></a>Observaciones

Para cambiar la información de conexión de una tabla adjunta, llame a [SetConnect](#setconnect) en el objeto de `CDaoTableDef` correspondiente y, a continuación, use la función miembro `RefreshLink` para actualizar la información. Cuando se llama a `RefreshLink`, no se cambian las propiedades de la tabla adjunta.

Para forzar que la información de conexión modificada surta efecto, deben cerrarse todos los objetos [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) abiertos basados en este objeto TableDef.

Para obtener información relacionada, vea el tema sobre el método RefreshLink en la ayuda de DAO.

##  <a name="setattributes"></a>CDaoTableDef:: SetAttributes

Establece un valor que indica una o más características de un objeto `CDaoTableDef`.

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parámetros

*lAttributes*<br/>
Características de la tabla representada por el objeto `CDaoTableDef` y puede ser una suma de estas constantes:

|Constante|Descripción|
|--------------|-----------------|
|`dbAttachExclusive`|En el caso de las bases de datos que usan el motor de base de datos de Microsoft Jet, indica que la tabla es una tabla adjunta abierta para uso exclusivo.|
|`dbAttachSavePWD`|En el caso de las bases de datos que usan el motor de base de datos de Microsoft Jet, indica que el ID. de usuario y la contraseña de la tabla adjunta se guardan con la información de conexión.|
|`dbSystemObject`|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos de Microsoft Jet.|
|`dbHiddenObject`|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos de Microsoft Jet.|

### <a name="remarks"></a>Observaciones

Al establecer varios atributos, puede combinarlos mediante la suma de las constantes adecuadas mediante el operador OR bit a bit. La configuración de `dbAttachExclusive` en una tabla no adjunta produce una excepción. La combinación de los siguientes valores también produce una excepción:

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Para obtener información relacionada, vea el tema "propiedad Attributes" en la ayuda de DAO.

##  <a name="setconnect"></a>CDaoTableDef:: SetConnect

Para un objeto `CDaoTableDef` que representa una tabla adjunta, el objeto de cadena se compone de una o dos partes (un especificador de tipo de base de datos y una ruta de acceso a la base de datos).

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parámetros

*lpszConnect*<br/>
Puntero a una expresión de cadena que especifica los parámetros adicionales que se van a pasar a los controladores de ODBC o ISAM instalables.

### <a name="remarks"></a>Observaciones

La ruta de acceso tal como se muestra en la tabla siguiente es la ruta de acceso completa del directorio que contiene los archivos de base de datos y debe ir precedida del identificador "DATABASE =". En algunos casos (al igual que con las bases de datos de Microsoft Jet y Microsoft Excel), se incluye un nombre de archivo específico en el argumento de ruta de acceso de la base de datos.

> [!NOTE]
>  No incluya espacios en blanco en las instrucciones de la ruta de acceso de signo igual de la forma "base de datos = unidad:\\\ruta". Esto producirá una excepción y se producirá un error en la conexión.

En la tabla siguiente se muestran los posibles tipos de base de datos y sus especificadores y rutas de acceso de base de datos correspondientes:

|Tipo de base de datos|Especificador|Path|
|-------------------|---------------|----------|
|Base de datos que usa el motor de base de datos Jet|"[`database`];"|"`drive`:\\*ruta de acceso* \ \\\ *nombre de archivo*. MDB|
|dBASE III|"dBASE III;"|"`drive`:\\\ *ruta de acceso*"|
|dBASE IV|"dBASE IV;"|"`drive`:\\\ *ruta de acceso*"|
|dBASE 5|"dBASE 5,0;"|"`drive`:\\\ *ruta de acceso*"|
|Paradox 3. x|"Paradox 3. x;"|"`drive`:\\\ *ruta de acceso*"|
|Paradox 4. x|"Paradox 4. x;"|"`drive`:\\\ *ruta de acceso*"|
|Paradox 5. x|"Paradox 5. x;"|"`drive`:\\\ *ruta de acceso*"|
|Excel 3.0|"Excel 3,0;"|"`drive`:\\*ruta de acceso* \ \\\ *nombre de archivo*. VACÍO|
|Excel 4,0|"Excel 4,0;"|"`drive`:\\*ruta de acceso* \ \\\ *nombre de archivo*. VACÍO|
|Excel 5,0 o Excel 95|"Excel 5,0;"|"`drive`:\\*ruta de acceso* \ \\\ *nombre de archivo*. VACÍO|
|Excel 97|"Excel 8,0;"|"`drive`:\\\ *ruta de acceso*\ *nombre de archivo*. VACÍO|
|Importación de HTML|"Importación de HTML"|"`drive`:\\\ *ruta de acceso*\ *nombreDeArchivo*"|
|Exportación de HTML|"Exportación de HTML"|"`drive`:\\\ *ruta de acceso*"|
|Texto|"Text;"|"unidad:\\\ruta"|
|ODBC|OBDC DATABASE = `database`; UID = *usuario*; PWD = *contraseña*; DSN = *datasourcename;* LOGINTIMEOUT = *segundos;* " (Puede que no sea una cadena de conexión completa para todos los servidores; es solo un ejemplo. Es muy importante no tener espacios entre los parámetros).|None|
|Exchange|Cambio<br /><br /> MAPILEVEL = *folderPath*;<br /><br /> [TABLETYPE = {0 &#124; 1};]<br /><br /> [PROFILE = *perfil*;]<br /><br /> [PWD = *contraseña*;]<br /><br /> [DATABASE = `database`;] "|*"unidad*:\\\ *ruta de acceso*\\\ *nombre de archivo*. MDB|

> [!NOTE]
>  Ya no se admite Btrieve desde DAO 3,5.

Debe usar una doble barra diagonal inversa (\\\\) en las cadenas de conexión. Si ha modificado las propiedades de una conexión existente mediante `SetConnect`, debe llamar a [RefreshLink](#refreshlink)posteriormente. Si va a inicializar las propiedades de conexión mediante `SetConnect`, no necesita llamar a `RefreshLink`, pero si decide hacerlo, anexe primero el objeto TableDef.

Si se requiere una contraseña, pero no se proporciona, el controlador ODBC muestra un cuadro de diálogo de inicio de sesión la primera vez que se tiene acceso a una tabla y de nuevo si la conexión se cierra y se vuelve a abrir.

Puede establecer la cadena de conexión para un objeto `CDaoTableDef` proporcionando un argumento de origen a la función miembro `Create`. Puede comprobar la configuración para determinar el tipo, la ruta de acceso, el ID. de usuario, la contraseña o el origen de datos ODBC de la base de datos. Para obtener más información, consulte la documentación del controlador específico.

Para obtener información relacionada, vea el tema "propiedad de conexión" en la ayuda de DAO.

##  <a name="setname"></a>CDaoTableDef:: SetName

Llame a esta función miembro para establecer un nombre definido por el usuario para una tabla.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una expresión de cadena que especifica el nombre de una tabla.

### <a name="remarks"></a>Observaciones

El nombre debe empezar por una letra y puede contener un máximo de 64 caracteres. Puede incluir números y caracteres de subrayado, pero no puede incluir signos de puntuación ni espacios.

Para obtener información relacionada, vea el tema "propiedad de nombre" en la ayuda de DAO.

##  <a name="setsourcetablename"></a>CDaoTableDef:: SetSourceTableName

Llame a esta función miembro para especificar el nombre de una tabla adjunta o el nombre de la tabla base en la que se basa el objeto `CDaoTableDef`, tal como existe en el origen inicial de los datos.

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parámetros

*lpszSrcTableName*<br/>
Un puntero a una expresión de cadena que especifica un nombre de tabla en la base de datos externa. En el caso de una tabla base, el valor es una cadena vacía ("").

### <a name="remarks"></a>Observaciones

A continuación, debe llamar a [RefreshLink](#refreshlink). Esta configuración de propiedad está vacía para una tabla base y de lectura y escritura para una tabla adjunta o un objeto no anexado a una colección.

Para obtener información relacionada, vea el tema "propiedad SourceTableName" en la ayuda de DAO.

##  <a name="setvalidationrule"></a>CDaoTableDef:: SetValidationRule

Llame a esta función miembro para establecer una regla de validación para una definición de grupo.

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parámetros

*lpszValidationRule*<br/>
Un puntero a una expresión de cadena que valida una operación.

### <a name="remarks"></a>Observaciones

Las reglas de validación se usan en relación con las operaciones de actualización. Si un TableDef contiene una regla de validación, las actualizaciones de ese TableDef deben coincidir con los criterios predeterminados antes de que se cambien los datos. Si el cambio no coincide con los criterios, se muestra una excepción que contiene el texto de [GetValidationText](#getvalidationtext) .

La validación solo se admite para las bases de datos que usan el motor de base de datos de Microsoft Jet. La expresión no puede hacer referencia a funciones definidas por el usuario, funciones de agregado de dominio, funciones de agregado de SQL o consultas. Una regla de validación para un objeto `CDaoTableDef` puede hacer referencia a varios campos de ese objeto.

Por ejemplo, para los campos denominados *hire_date* y *termination_date*, una regla de validación podría ser:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Para obtener información relacionada, vea el tema "propiedad ValidationRule" en la ayuda de DAO.

##  <a name="setvalidationtext"></a>CDaoTableDef:: SetValidationText

Llame a esta función miembro para establecer el texto de la excepción de una regla de validación para un objeto `CDaoTableDef` con una tabla base subyacente compatible con el motor de base de datos de Microsoft Jet.

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parámetros

*lpszValidationText*<br/>
Un puntero a una expresión de cadena que especifica el texto que se muestra si los datos especificados no son válidos.

### <a name="remarks"></a>Observaciones

No se puede establecer el texto de validación de una tabla adjunta.

Para obtener información relacionada, vea el tema "propiedad ValidationText" en la ayuda de DAO.

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)
