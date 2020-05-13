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
ms.openlocfilehash: adc31ccbf2be34aa1df1fa56111d1990701a6329
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754689"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef (clase)

Representa la definición almacenada de una tabla base o una tabla asociada.

## <a name="syntax"></a>Sintaxis

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Construye un objeto `CDaoTableDef`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoTableDef::Append](#append)|Agrega una nueva tabla a la base de datos.|
|[CDaoTableDef::CanUpdate](#canupdate)|Devuelve distinto de cero si se puede actualizar la tabla (puede modificar la definición de campos o las propiedades de la tabla).|
|[CDaoTableDef::Cerrar](#close)|Cierra una entrada de tabla abierta.|
|[CDaoTableDef::Crear](#create)|Crea una tabla que se puede agregar a la base de datos mediante [Anexar](#append).|
|[CDaoTableDef::CreateField](#createfield)|Se llama para crear un campo para una tabla.|
|[CDaoTableDef::CreateIndex](#createindex)|Se llama para crear un índice para una tabla.|
|[CDaoTableDef::DeleteField](#deletefield)|Se llama para eliminar un campo de una tabla.|
|[CDaoTableDef::DeleteIndex](#deleteindex)|Se llama para eliminar un índice de una tabla.|
|[CDaoTableDef::GetAttributes](#getattributes)|Devuelve un valor que indica una `CDaoTableDef` o varias características de un objeto.|
|[CDaoTableDef::GetConnect](#getconnect)|Devuelve un valor que proporciona información sobre el origen de una tabla.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Devuelve la fecha y hora en `CDaoTableDef` que se creó la tabla base subyacente a un objeto.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha y hora del cambio más reciente realizado en el diseño de la tabla base.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Devuelve un valor que representa el número de campos de la tabla.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Devuelve tipos específicos de información sobre los campos de la tabla.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Devuelve el número de índices de la tabla.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Devuelve tipos específicos de información sobre los índices de la tabla.|
|[CDaoTableDef::GetName](#getname)|Devuelve el nombre definido por el usuario de la tabla.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Devuelve el número de registros de la tabla.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Devuelve un valor que especifica el nombre de la tabla adjunta en la base de datos de origen.|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Devuelve un valor que valida los datos de un campo a medida que se cambian o se agregan a una tabla.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Devuelve un valor que especifica el texto del mensaje que muestra la aplicación si el valor de un objeto Field no satisface la regla de validación especificada.|
|[CDaoTableDef::IsOpen](#isopen)|Devuelve distinto de cero si la tabla está abierta.|
|[CDaoTableDef::Open](#open)|Abre una base de datos existente almacenada en la colección TableDef de la base de datos.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Actualiza la información de conexión de una tabla adjunta.|
|[CDaoTableDef::SetAttributes](#setattributes)|Establece un valor que indica una `CDaoTableDef` o varias características de un objeto.|
|[CDaoTableDef::SetConnect](#setconnect)|Establece un valor que proporciona información sobre el origen de una tabla.|
|[CDaoTableDef::SetName](#setname)|Establece el nombre de la tabla.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Establece un valor que especifica el nombre de una tabla adjunta en la base de datos de origen.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Establece un valor que valida los datos de un campo a medida que se cambian o se agregan a una tabla.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Establece un valor que especifica el texto del mensaje que muestra la aplicación si el valor de un objeto Field no satisface la regla de validación especificada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Puntero a la interfaz DAO subyacente al objeto tabledef.|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Base de datos de origen para esta tabla.|

## <a name="remarks"></a>Observaciones

Cada objeto de base de datos DAO mantiene una colección, denominada TableDefs, que contiene todos los objetos de base de tabla DAO guardados.

Manipular una definición `CDaoTableDef` de tabla mediante un objeto. Por ejemplo, puede:

- Examine la estructura de campo e índice de cualquier tabla local, adjunta o externa de una base de datos.

- Llame `SetConnect` a `SetSourceTableName` las funciones miembro y `RefreshLink` para las tablas adjuntas y use la función miembro para actualizar las conexiones a las tablas adjuntas.

- Llame `CanUpdate` a la función miembro para determinar si puede editar definiciones de campo en la tabla.

- Obtener o establecer condiciones `GetValidationRule` `SetValidationRule`de validación `SetValidationText` mediante las funciones y miembro y y . `GetValidationText`

- Utilice `Open` la función miembro para crear un objeto de `CDaoRecordset` tipo tabla, conjunto de registros dinámicos o instantánea.

    > [!NOTE]
    >  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO; las clases DAO generalmente ofrecen capacidades superiores porque son específicas del motor de base de datos Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Para utilizar objetos de base de tabla para trabajar con una tabla existente o para crear una nueva tabla

1. En todos los casos, primero construir un `CDaoTableDef` objeto, proporcionando un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto al que pertenece la tabla.

1. A continuación, haga lo siguiente, dependiendo de lo que desee:

   - Para utilizar una tabla guardada existente, llame a la función miembro [Open](#open) del objeto tabledef, proporcionando el nombre de la tabla guardada.

   - Para crear una nueva tabla, llame a la tabledef del objeto [Create](#create) función miembro, proporcionando el nombre de la tabla. Llame a [CreateField](#createfield) y [CreateIndex](#createindex) para agregar campos e índices a la tabla.

   - Llame a [Append](#append) para guardar la tabla anexándola a la colección TableDefs de la base de datos. `Create`pone el tabledef en un estado `Create` abierto, por `Open`lo que después de llamar no llame a .

        > [!TIP]
        >  La forma más fácil de crear tablas guardadas es crearlas y almacenarlas en la base de datos mediante Microsoft Access. A continuación, puede abrirlos y usarlos en el código MFC.

Para utilizar el objeto tabledef que ha abierto `CDaoRecordset` o creado, cree y abra un `dbOpenTable` objeto, especificando el nombre de la referencia de tabla con un valor en el parámetro *nOpenType.*

Para utilizar un objeto tabledef para crear un `CDaoRecordset` objeto, normalmente se crea o se abre una desf de tabla como se ha descrito anteriormente y, a continuación, se construye un objeto de conjunto de registros, pasando un puntero al objeto tabledef cuando se llama a [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). La tabla que pase debe estar en un estado abierto. Para obtener más información, vea la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Cuando termine de usar un objeto tabledef, llame a su [Close](../../mfc/reference/cdaorecordset-class.md#close) función miembro; a continuación, destruir el objeto tabledef.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="cdaotabledefappend"></a><a name="append"></a>CDaoTableDef::Append

Llame a esta función miembro después de llamar a [Crear](#create) para crear un nuevo objeto tabledef para guardar la propiedad de tabla en la base de datos.

```
virtual void Append();
```

### <a name="remarks"></a>Observaciones

La función anexa el objeto a la colección TableDefs de la base de datos. Puede utilizar la definición de tabla como un objeto temporal al definirla no anexionándola, `Append`pero si desea guardarla y utilizarla, debe llamar a .

> [!NOTE]
> Si intenta anexar una conversión de tabla sin nombre (que contiene una cadena nula o vacía), MFC produce una excepción.

Para obtener información relacionada, vea el tema "Método de anexar" en la Ayuda de DAO.

## <a name="cdaotabledefcanupdate"></a><a name="canupdate"></a>CDaoTableDef::CanUpdate

Llame a esta función miembro para determinar `CDaoTableDef` si se puede cambiar la definición de la tabla subyacente a un objeto.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se puede modificar la estructura de tabla (esquema) (añadir o eliminar campos e índices), en caso contrario 0.

### <a name="remarks"></a>Observaciones

De forma predeterminada, se puede `CDaoTableDef` actualizar una tabla recién creada subyacente `CDaoTableDef` a un objeto y no se puede actualizar una tabla adjunta subyacente a un objeto. Un `CDaoTableDef` objeto puede ser actualizable, incluso si el conjunto de registros resultante no es actualizable.

Para obtener información relacionada, vea el tema "Propiedad actualizable" en la Ayuda de DAO.

## <a name="cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef

Construye un objeto `CDaoTableDef`.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parámetros

*pBase de datos*<br/>
Un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.

### <a name="remarks"></a>Observaciones

Después de construir el objeto, debe llamar a la [Create](#create) o [Open](#open) función miembro. Cuando termine con el objeto, [Close](#close) debe llamar a `CDaoTableDef` su Close función miembro y destruir el objeto.

## <a name="cdaotabledefclose"></a><a name="close"></a>CDaoTableDef::Cerrar

Llame a esta función miembro para cerrar y liberar el objeto tabledef.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Normalmente, `Close`después de llamar a , se elimina el objeto tabledef si se asignó con **new**.

Puede llamar [Open](#open) a Abrir `Close`de nuevo después de llamar . Esto le permite reutilizar el objeto tabledef.

Para obtener información relacionada, vea el tema "Método de cierre" en la Ayuda de DAO.

## <a name="cdaotabledefcreate"></a><a name="create"></a>CDaoTableDef::Crear

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
Valor correspondiente a las características de la tabla representada por el objeto tabledef. Puede utilizar bit a bit-OR para combinar cualquiera de las siguientes constantes:

|Constante|Descripción|
|--------------|-----------------|
|`dbAttachExclusive`|Para las bases de datos que usan el motor de base de datos Microsoft Jet, indica que la tabla es una tabla adjunta abierta para uso exclusivo.|
|`dbAttachSavePWD`|Para las bases de datos que usan el motor de base de datos microsoft Jet, indica que el identificador de usuario y la contraseña de la tabla adjunta se guardan con la información de conexión.|
|`dbSystemObject`|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet.|
|`dbHiddenObject`|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet.|

*lpszSrcTable*<br/>
Puntero a una cadena que contiene el nombre de la tabla de origen. De forma predeterminada, este valor se inicializa como NULL.

*lpszConnect*<br/>
Puntero a una cadena que contiene la cadena de conexión predeterminada. De forma predeterminada, este valor se inicializa como NULL.

### <a name="remarks"></a>Observaciones

Una vez que haya nombrado la base de datos, puede llamar a [Append](#append) para guardar la tabledef en la colección TableDefs de la base de datos. Después `Append`de llamar a , la conversa de datos de tabla está en un estado abierto y puede usarla para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto.

Para obtener información relacionada, vea el tema "Método CreateTableDef" en la Ayuda de DAO.

## <a name="cdaotabledefcreatefield"></a><a name="createfield"></a>CDaoTableDef::CreateField

Llame a esta función miembro para agregar un campo a la tabla.

```cpp
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una expresión de cadena que especifique el nombre de este campo.

*nType*<br/>
Valor que indica el tipo de datos del campo. La configuración puede ser uno de estos valores:

|Tipo|Tamaño (bytes)|Descripción|
|----------|--------------------|-----------------|
|`dbBoolean`|1 byte|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|Moneda ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|FLOAT|
|`dbDouble`|8|double|
|`dbDate`|8|Fecha/Hora ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texto ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (objeto OLE), [CLongBinary](../../mfc/reference/clongbinary-class.md) o [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Memo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Valor que indica el tamaño máximo, en bytes, de un campo que contiene texto o el tamaño fijo de un campo que contiene texto o valores numéricos. El parámetro *lSize* se omite para todos los campos excepto texto.

*lAttributes*<br/>
Un valor correspondiente a las características del campo y que se puede combinar mediante un OR bit a bit.

|Constante|Descripción|
|--------------|-----------------|
|`dbFixedField`|El tamaño del campo es fijo (predeterminado para los campos numéricos).|
|`dbVariableField`|El tamaño del campo es variable (solo campos de texto).|
|`dbAutoIncrField`|El valor de campo para los nuevos registros se incrementa automáticamente en un entero largo único que no se puede cambiar. Solo se admite para tablas de base de datos de Microsoft Jet.|
|`dbUpdatableField`|El valor del campo se puede cambiar.|
|`dbDescending`|El campo se ordena en orden descendente (Z - A o 100 - 0) (solo se aplica a un objeto Field de una colección Fields de un objeto Index). Si omite esta constante, el campo se ordena en orden ascendente (A - Z o 0 - 100) (predeterminado).|

*fieldinfo*<br/>
Una referencia a un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura.

### <a name="remarks"></a>Observaciones

Se `DAOField` crea un objeto (OLE) y se `DAOTableDef` anexa a la colección Fields del objeto (OLE). Además de su uso para examinar `CDaoFieldInfo` las propiedades del objeto, también puede utilizar para construir un parámetro de entrada para crear nuevos campos en una referencia de tabla. La primera `CreateField` versión de es más fácil de usar, pero si desea `CreateField`un control `CDaoFieldInfo` más preciso, puede utilizar la segunda versión de , que toma un parámetro.

Si utiliza la `CreateField` versión `CDaoFieldInfo` de que toma un parámetro, debe `CDaoFieldInfo` establecer cuidadosamente cada uno de los siguientes miembros de la estructura:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Los miembros `CDaoFieldInfo` restantes de deben establecerse en **0**, FALSE, o `CDaoException` una cadena vacía, según corresponda para el miembro, o puede ocurrir un.

Para obtener información relacionada, vea el tema "Método CreateField" en la Ayuda de DAO.

## <a name="cdaotabledefcreateindex"></a><a name="createindex"></a>CDaoTableDef::CreateIndex

Llame a esta función para agregar un índice a una tabla.

```cpp
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parámetros

*indexinfo*<br/>
Una referencia a un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura.

### <a name="remarks"></a>Observaciones

Los índices especifican el orden de los registros a los que se tiene acceso desde las tablas de base de datos y si se aceptan o no registros duplicados. Los índices también proporcionan un acceso eficaz a los datos.

No es necesario crear índices para tablas, pero en tablas grandes no indizadas, el acceso a un registro específico o la creación de un conjunto de registros puede tardar mucho tiempo. Por otro lado, la creación de demasiados índices ralentiza las operaciones de actualización, anexión y eliminación, ya que todos los índices se actualizan automáticamente. Tenga en cuenta estos factores a medida que decide qué índices crear.

Se deben establecer `CDaoIndexInfo` los siguientes miembros de la estructura:

- `m_strName`Se debe proporcionar un nombre.

- `m_pFieldInfos`Debe apuntar a `CDaoIndexFieldInfo` una matriz de estructuras.

- `m_nFields`Debe especificar el número de `CDaoFieldInfo` campos en la matriz de estructuras.

Los miembros restantes se omitirán si se establece en FALSE. Además, `m_lDistinctCount` el miembro se omite durante la creación del índice.

## <a name="cdaotabledefdeletefield"></a><a name="deletefield"></a>CDaoTableDef::DeleteField

Llame a esta función miembro para quitar un campo y hacerlo inaccesible.

```cpp
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una expresión de cadena que es el nombre de un campo existente.

*nIndex*<br/>
El índice del campo de la colección Fields de base cero de la tabla, para la búsqueda por índice.

### <a name="remarks"></a>Observaciones

Puede usar esta función miembro en un nuevo objeto que no se ha anexado a la base de datos o cuando [CanUpdate](#canupdate) devuelve distinto de cero.

Para obtener información relacionada, vea el tema "Método de eliminación" en la Ayuda de DAO.

## <a name="cdaotabledefdeleteindex"></a><a name="deleteindex"></a>CDaoTableDef::DeleteIndex

Llame a esta función miembro para eliminar un índice en una tabla subyacente.

```cpp
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una expresión de cadena que es el nombre de un índice existente.

*nIndex*<br/>
El índice de matriz del objeto de índice en la colección TableDefs de base cero de la base de datos, para la búsqueda por índice.

### <a name="remarks"></a>Observaciones

Puede usar esta función miembro en un nuevo objeto que no se ha anexado a la base de datos o cuando [CanUpdate](#canupdate) devuelve distinto de cero.

Para obtener información relacionada, vea el tema "Método de eliminación" en la Ayuda de DAO.

## <a name="cdaotabledefgetattributes"></a><a name="getattributes"></a>CDaoTableDef::GetAttributes

Para `CDaoTableDef` un objeto, el valor devuelto especifica las `CDaoTableDef` características de la tabla representada por el objeto y puede ser una suma de estas constantes:

```
long GetAttributes();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que indica una `CDaoTableDef` o varias características de un objeto.

### <a name="remarks"></a>Observaciones

|Constante|Descripción|
|--------------|-----------------|
|`dbAttachExclusive`|Para las bases de datos que usan el motor de base de datos Microsoft Jet, indica que la tabla es una tabla adjunta abierta para uso exclusivo.|
|`dbAttachSavePWD`|Para las bases de datos que usan el motor de base de datos microsoft Jet, indica que el identificador de usuario y la contraseña de la tabla adjunta se guardan con la información de conexión.|
|`dbSystemObject`|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet.|
|`dbHiddenObject`|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet.|
|`dbAttachedTable`|Indica que la tabla es una tabla adjunta de una base de datos no ODBC, como una base de datos Paradox.|
|`dbAttachedODBC`|Indica que la tabla es una tabla adjunta de una base de datos ODBC, como Microsoft SQL Server.|

Una tabla del sistema es una tabla creada por el motor de base de datos Microsoft Jet que contiene información interna.

Una tabla oculta es una tabla creada para uso temporal por el motor de base de datos Microsoft Jet.

Para obtener información relacionada, vea el tema "Propiedad de atributos" en la Ayuda de DAO.

## <a name="cdaotabledefgetconnect"></a><a name="getconnect"></a>CDaoTableDef::GetConnect

Llame a esta función miembro para obtener la cadena de conexión para un origen de datos.

```
CString GetConnect();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que contiene la ruta de acceso y el tipo de base de datos de la tabla.

### <a name="remarks"></a>Observaciones

Para `CDaoTableDef` un objeto que representa una `CString` tabla adjunta, el objeto consta de una o dos partes (un especificador de tipo de base de datos y una ruta de acceso a la base de datos).

La ruta de acceso como se muestra en la tabla siguiente es la ruta de acceso completa para el directorio que contiene los archivos de base de datos y debe ir precedida por el identificador "DATABASE". En algunos casos (como con las bases de datos de Microsoft Jet y Microsoft Excel), se incluye un nombre de archivo específico en el argumento de ruta de acceso de base de datos.

La tabla de [CDaoTableDef::SetConnect](#setconnect) muestra los posibles tipos de base de datos y sus especificadores y rutas de acceso de base de datos correspondientes:

Para las tablas base de base de base de base de base de Microsoft Jet, el especificador es una cadena vacía ("").

Si se requiere una contraseña pero no se proporciona, el controlador ODBC muestra un cuadro de diálogo de inicio de sesión la primera vez que se accede a una tabla y de nuevo si la conexión se cierra y se vuelve a abrir. Si una tabla `dbAttachSavePWD` adjunta tiene el atributo, la solicitud de inicio de sesión no aparecerá cuando se vuelva a abrir la tabla.

Para obtener información relacionada, vea el tema "Conectar propiedad" en la Ayuda de DAO.

## <a name="cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a>CDaoTableDef::GetDateCreated

Llame a esta función para determinar la `CDaoTableDef` fecha y hora en que se creó la tabla subyacente al objeto.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valor devuelto

Valor que contiene la fecha y la hora `CDaoTableDef` de la creación de la tabla subyacente al objeto.

### <a name="remarks"></a>Observaciones

La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la tabla base. En un entorno multiusuario, los usuarios deben obtener esta configuración directamente desde el servidor de archivos para evitar discrepancias; es decir, todos los clientes deben usar un origen de tiempo "estándar", tal vez desde un servidor.

Para obtener información relacionada, vea el tema "DateCreated, LastUpdated Properties" en la Ayuda de DAO.

## <a name="cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated

Llame a esta función para determinar la `CDaoTableDef` fecha y hora en que se actualizó por última vez la tabla subyacente al objeto.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valor devuelto

Valor que contiene la fecha y hora `CDaoTableDef` en que se actualizó por última vez la tabla subyacente al objeto.

### <a name="remarks"></a>Observaciones

La configuración de fecha y hora se deriva del equipo en el que se creó o actualizó por última vez la tabla base. En un entorno multiusuario, los usuarios deben obtener esta configuración directamente desde el servidor de archivos para evitar discrepancias; es decir, todos los clientes deben usar un origen de tiempo "estándar", tal vez desde un servidor.

Para obtener información relacionada, vea el tema "DateCreated, LastUpdated Properties" en la Ayuda de DAO.

## <a name="cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a>CDaoTableDef::GetFieldCount

Llame a esta función miembro para recuperar el número de campos definidos en la tabla.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valor devuelto

El número de campos de la tabla.

### <a name="remarks"></a>Observaciones

Si su valor es 0, no hay objetos en la colección.

Para obtener información relacionada, vea el tema "Count Property" en la Ayuda de DAO.

## <a name="cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo

Llame a esta función miembro para obtener varios tipos de información sobre un campo definido en la definición de tabla.

```cpp
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
El índice del objeto de campo de la colección Fields de base cero de la tabla, para la búsqueda por índice.

*fieldinfo*<br/>
Una referencia a un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el campo se va a recuperar. Las opciones disponibles se enumeran aquí junto con lo que hacen que la función devuelva:

- `AFX_DAO_PRIMARY_INFO`(Predeterminado) Nombre, Tipo, Tamaño, Atributos. Utilice esta opción para obtener el rendimiento más rápido.

- `AFX_DAO_SECONDARY_INFO`Información principal, además de: Posición ordinal, Requerido, Permitir longitud cero, Orden de intercalación, Nombre externo, Campo de origen, Tabla de origen

- `AFX_DAO_ALL_INFO`Información primaria y secundaria, además de: Regla de validación, Texto de validación, Valor predeterminado

*lpszName*<br/>
Un puntero al nombre del objeto de campo, para la búsqueda por nombre. El nombre es una cadena con hasta 64 caracteres que nombra de forma única el campo.

### <a name="remarks"></a>Observaciones

Una versión de la función le permite buscar un campo por índice. La otra versión le permite buscar un campo por nombre.

Para obtener una descripción de la información devuelta, vea el [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de *dwInfoOptions*. Cuando solicita información en un nivel, también obtiene información para cualquier nivel anterior.

Para obtener información relacionada, vea el tema "Propiedad de atributos" en la Ayuda de DAO.

## <a name="cdaotabledefgetindexcount"></a><a name="getindexcount"></a>CDaoTableDef::GetIndexCount

Llame a esta función miembro para obtener el número de índices de una tabla.

```
short GetIndexCount();
```

### <a name="return-value"></a>Valor devuelto

El número de índices de la tabla.

### <a name="remarks"></a>Observaciones

Si su valor es 0, no hay índices en la colección.

Para obtener información relacionada, vea el tema "Count Property" en la Ayuda de DAO.

## <a name="cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo

Llame a esta función miembro para obtener varios tipos de información sobre un índice definido en la definición de tabla.

```cpp
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
El índice numérico del objeto Index de la colección Indexes de base cero de la tabla, para buscar por su posición en la colección.

*indexinfo*<br/>
Una referencia a un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura.

*dwInfoOptions*<br/>
Opciones que especifican qué información sobre el índice se va a recuperar. Las opciones disponibles se enumeran aquí junto con lo que hacen que la función devuelva:

- `AFX_DAO_PRIMARY_INFO`Nombre, Información de campo, Campos. Utilice esta opción para obtener el rendimiento más rápido.

- `AFX_DAO_SECONDARY_INFO`Información primaria, además de: Primaria, Única, Agrupada, Ignorar Nulos, Obligatoria, Extranjera

- `AFX_DAO_ALL_INFO`Información primaria y secundaria, además: Recuento diferenciado

*lpszName*<br/>
Un puntero al nombre del objeto de índice, para la búsqueda por nombre.

### <a name="remarks"></a>Observaciones

Una versión de la función permite buscar un índice por su posición en la colección. La otra versión le permite buscar un índice por nombre.

Para obtener una descripción de la información devuelta, vea el [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura. Esta estructura tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de *dwInfoOptions*. Cuando solicita información en un nivel, también obtiene información para cualquier nivel anterior.

Para obtener información relacionada, vea el tema "Propiedad de atributos" en la Ayuda de DAO.

## <a name="cdaotabledefgetname"></a><a name="getname"></a>CDaoTableDef::GetName

Llame a esta función miembro para obtener el nombre definido por el usuario de la tabla subyacente.

```
CString GetName();
```

### <a name="return-value"></a>Valor devuelto

Un nombre definido por el usuario para una tabla.

### <a name="remarks"></a>Observaciones

Este nombre comienza con una letra y puede contener un máximo de 64 caracteres. Puede incluir números y caracteres de subrayado, pero no puede incluir puntuación ni espacios.

Para obtener información relacionada, vea el tema "Propiedad de nombre" en la Ayuda de DAO.

## <a name="cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a>CDaoTableDef::GetRecordCount

Llame a esta función miembro para `CDaoTableDef` averiguar cuántos registros hay en un objeto.

```
long GetRecordCount();
```

### <a name="return-value"></a>Valor devuelto

El número de registros a los que se tiene acceso en un objeto tabledef.

### <a name="remarks"></a>Observaciones

Llamar `GetRecordCount` a un `CDaoTableDef` objeto de tipo tabla refleja el número aproximado de registros de la tabla y se ve afectado inmediatamente a medida que se agregan y eliminan registros de tabla. Las transacciones revertidas aparecerán como parte del recuento de registros hasta que llame a [CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). Un `CDaoTableDef` objeto sin registros tiene un valor de propiedad de recuento de registros de 0. Cuando se trabaja con tablas adjuntas o bases de datos ODBC, `GetRecordCount` siempre devuelve -1.

Para obtener información relacionada, vea el tema "Propiedad RecordCount" en la Ayuda de DAO.

## <a name="cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName

Llame a esta función miembro para recuperar el nombre de una tabla adjunta en una base de datos de origen.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que especifica el nombre de origen de una tabla adjunta o una cadena vacía si una tabla de datos nativa.

### <a name="remarks"></a>Observaciones

Una tabla adjunta es una tabla de otra base de datos vinculada a una base de datos de Microsoft Jet. Los datos de las tablas adjuntas permanecen en la base de datos externa, donde pueden ser manipulados por otras aplicaciones.

Para obtener información relacionada, vea el tema "SourceTableName (propiedad) en la Ayuda de DAO.

## <a name="cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule

Llame a esta función miembro para recuperar la regla de validación para una conversión de tabla.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que valida los datos de un campo a medida que se cambian o se agregan a una tabla.

### <a name="remarks"></a>Observaciones

Las reglas de validación se utilizan en relación con las operaciones de actualización. Si una hoja de datos contiene una regla de validación, las actualizaciones de esa hoja de discos deben coincidir con criterios predeterminados antes de cambiar los datos. Si el cambio no coincide con los criterios, se produce una excepción que contiene el valor de [GetValidationText.](#getvalidationtext) Para `CDaoTableDef` un objeto, esto `CString` es de solo lectura para una tabla adjunta y de lectura y escritura para una tabla base.

Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.

## <a name="cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoTableDef::GetValidationText

Llame a esta función para recuperar la cadena que se va a mostrar cuando un usuario escribe datos que no coinciden con la regla de validación.

```
CString GetValidationText();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que especifica el texto que se muestra si el usuario escribe datos que no coinciden con la regla de validación.

### <a name="remarks"></a>Observaciones

Para `CDaoTableDef` un objeto, esto `CString` es de solo lectura para una tabla adjunta y de lectura y escritura para una tabla base.

Para obtener información relacionada, vea el tema "Propiedad ValidationText" en la Ayuda de DAO.

## <a name="cdaotabledefisopen"></a><a name="isopen"></a>CDaoTableDef::IsOpen

Llame a esta función `CDaoTableDef` miembro para determinar si el objeto está abierto actualmente.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de `CDaoTableDef` cero si el objeto está abierto; de lo contrario 0.

### <a name="remarks"></a>Observaciones

## <a name="cdaotabledefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase

Contiene un puntero a la [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto para esta tabla.

### <a name="remarks"></a>Observaciones

## <a name="cdaotabledefm_pdaotabledef"></a><a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef

Contiene un puntero a la interfaz OLE para `CDaoTableDef` el objeto de def de tabla DAO subyacente al objeto.

### <a name="remarks"></a>Observaciones

Utilice este puntero si necesita acceder a la interfaz DAO directamente.

## <a name="cdaotabledefopen"></a><a name="open"></a>CDaoTableDef::Open

Llame a esta función miembro para abrir una tabladef previamente guardada en la colección TableDef de la base de datos.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una cadena que especifica un nombre de tabla.

### <a name="remarks"></a>Observaciones

## <a name="cdaotabledefrefreshlink"></a><a name="refreshlink"></a>CDaoTableDef::RefreshLink

Llame a esta función miembro para actualizar la información de conexión de una tabla adjunta.

```cpp
void RefreshLink();
```

### <a name="remarks"></a>Observaciones

Cambiar la información de conexión de una tabla `CDaoTableDef` adjunta mediante una `RefreshLink` llamada a [SetConnect](#setconnect) en el objeto correspondiente y, a continuación, mediante la función miembro para actualizar la información. Cuando se `RefreshLink`llama a , las propiedades de la tabla adjunta no se cambian.

Para forzar que la información de conexión modificada surta efecto, todos los objetos [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) abiertos basados en esta base de tabla deben estar cerrados.

Para obtener información relacionada, vea el tema "Método RefreshLink" en la Ayuda de DAO.

## <a name="cdaotabledefsetattributes"></a><a name="setattributes"></a>CDaoTableDef::SetAttributes

Establece un valor que indica una `CDaoTableDef` o varias características de un objeto.

```cpp
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parámetros

*lAttributes*<br/>
Características de la tabla `CDaoTableDef` representada por el objeto y puede ser una suma de estas constantes:

|Constante|Descripción|
|--------------|-----------------|
|`dbAttachExclusive`|Para las bases de datos que usan el motor de base de datos Microsoft Jet, indica que la tabla es una tabla adjunta abierta para uso exclusivo.|
|`dbAttachSavePWD`|Para las bases de datos que usan el motor de base de datos microsoft Jet, indica que el identificador de usuario y la contraseña de la tabla adjunta se guardan con la información de conexión.|
|`dbSystemObject`|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet.|
|`dbHiddenObject`|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet.|

### <a name="remarks"></a>Observaciones

Al establecer varios atributos, puede combinarlos sumando las constantes adecuadas mediante el operador OR bit a bit. Establecer `dbAttachExclusive` en una tabla no adjunta produce una excepción. La combinación de los siguientes valores también produce una excepción:

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Para obtener información relacionada, vea el tema "Propiedad de atributos" en la Ayuda de DAO.

## <a name="cdaotabledefsetconnect"></a><a name="setconnect"></a>CDaoTableDef::SetConnect

Para `CDaoTableDef` un objeto que representa una tabla adjunta, el objeto de cadena consta de una o dos partes (un especificador de tipo de base de datos y una ruta de acceso a la base de datos).

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parámetros

*lpszConnect*<br/>
Puntero a una expresión de cadena que especifica parámetros adicionales para pasar a ODBC o controladores ISAM instalables.

### <a name="remarks"></a>Observaciones

La ruta de acceso como se muestra en la tabla siguiente es la ruta de acceso completa para el directorio que contiene los archivos de base de datos y debe ir precedida por el identificador "DATABASE". En algunos casos (como con las bases de datos de Microsoft Jet y Microsoft Excel), se incluye un nombre de archivo específico en el argumento de ruta de acceso de base de datos.

> [!NOTE]
> No incluya espacios en blanco alrededor de las instrucciones de ruta\\de acceso de inicio de sesión igual de la forma "DATABASE-drive: .path". Esto dará lugar a una excepción y la conexión falla.

En la tabla siguiente se muestran los posibles tipos de base de datos y sus especificadores y rutas de acceso de base de datos correspondientes:

|Tipo de base de datos|Especificador|Path|
|-------------------|---------------|----------|
|Base de datos utilizando el motor de base de datos Jet|"[ `database`];"|" `drive`\\\ : nombre*de archivo*de*ruta*\\\ . MDB"|
|dBASE III|"dBASE III;"|" `drive`\\\ :*camino*"|
|dBASE IV|"dBASE IV;"|" `drive`\\\ :*camino*"|
|dBASE 5|"dBASE 5.0;"|" `drive`\\\ :*camino*"|
|Paradoja 3.x|"Paradoja 3.x;"|" `drive`\\\ :*camino*"|
|Paradoja 4.x|"Paradoja 4.x;"|" `drive`\\\ :*camino*"|
|Paradoja 5.x|"Paradoja 5.x;"|" `drive`\\\ :*camino*"|
|Excel 3.0|"Excel 3.0;"|" `drive`\\\ : nombre*de archivo*de*ruta*\\\ . XLS"|
|Excel 4.0|"Excel 4.0;"|" `drive`\\\ : nombre*de archivo*de*ruta*\\\ . XLS"|
|Excel 5.0 o Excel 95|"Excel 5.0;"|" `drive`\\\ : nombre*de archivo*de*ruta*\\\ . XLS"|
|Excel 97|"Excel 8.0;"|" `drive`\\\ : nombre*de archivo*de*ruta*\ . XLS"|
|Importación HTML|"Importación HTML;"|" `drive`\\\ : nombre*de archivo*de*ruta*\ "|
|Exportación HTML|"Exportación HTML;"|" `drive`\\\ :*camino*"|
|Texto|"Texto;"|"unidad:\\"ruta"|
|ODBC|"ODBC; BASE `database`DE DATOS ; Usuario UID *;* Contraseña PWD *;* *Nombredefuente* de datos DSN; LOGINTIMEOUT *SEGUNDOs;*" (Esto puede no ser una cadena de conexión completa para todos los servidores; es solo un ejemplo. Es muy importante no tener espacios entre los parámetros.)|None|
|Exchange|"Intercambio;<br /><br /> Ruta de acceso a *carpetas*MAPILEVEL ;<br /><br /> [TABLETYPE- 0 &#124; 1;]<br /><br /> [Perfil DE PERFIL *;]*<br /><br /> *[Contraseña*PWD ;]<br /><br /> [BASE `database`DE DATOS ;]"|*"drive*\\\ :*path*\\\ *filename*. MDB"|

> [!NOTE]
> Btrieve ya no es compatible con DAO 3.5.

Debe utilizar una barra\\\\diagonal inversa doble ( ) en las cadenas de conexión. Si ha modificado las propiedades de `SetConnect`una conexión existente mediante , debe llamar posteriormente a [RefreshLink](#refreshlink). Si va a inicializar las `SetConnect`propiedades de `RefreshLink`conexión mediante , no es necesario llamar a , pero si decide hacerlo, primero anexe la base de datos de tabla.

Si se requiere una contraseña pero no se proporciona, el controlador ODBC muestra un cuadro de diálogo de inicio de sesión la primera vez que se accede a una tabla y de nuevo si la conexión se cierra y se vuelve a abrir.

Puede establecer la cadena `CDaoTableDef` de conexión para un `Create` objeto proporcionando un argumento de origen a la función miembro. Puede comprobar la configuración para determinar el tipo, la ruta de acceso, el identificador de usuario, la contraseña o el origen de datos ODBC de la base de datos. Para obtener más información, consulte la documentación del controlador específico.

Para obtener información relacionada, vea el tema "Conectar propiedad" en la Ayuda de DAO.

## <a name="cdaotabledefsetname"></a><a name="setname"></a>CDaoTableDef::SetName

Llame a esta función miembro para establecer un nombre definido por el usuario para una tabla.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una expresión de cadena que especifica un nombre para una tabla.

### <a name="remarks"></a>Observaciones

El nombre debe comenzar con una letra y puede contener un máximo de 64 caracteres. Puede incluir números y caracteres de subrayado, pero no puede incluir puntuación ni espacios.

Para obtener información relacionada, vea el tema "Propiedad de nombre" en la Ayuda de DAO.

## <a name="cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName

Llame a esta función miembro para especificar el nombre de una `CDaoTableDef` tabla adjunta o el nombre de la tabla base en la que se basa el objeto, ya que existe en el origen original de los datos.

```cpp
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parámetros

*lpszSrcTableName*<br/>
Puntero a una expresión de cadena que especifica un nombre de tabla en la base de datos externa. Para una tabla base, la configuración es una cadena vacía ("").

### <a name="remarks"></a>Observaciones

A continuación, debe llamar a [RefreshLink](#refreshlink). Este valor de propiedad está vacío para una tabla base y de lectura y escritura para una tabla adjunta o un objeto no anexado a una colección.

Para obtener información relacionada, vea el tema "SourceTableName (propiedad) en la Ayuda de DAO.

## <a name="cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule

Llame a esta función miembro para establecer una regla de validación para una conversión de tabla.

```cpp
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parámetros

*lpszValidationRule*<br/>
Puntero a una expresión de cadena que valida una operación.

### <a name="remarks"></a>Observaciones

Las reglas de validación se utilizan en relación con las operaciones de actualización. Si una hoja de datos contiene una regla de validación, las actualizaciones de esa hoja de discos deben coincidir con criterios predeterminados antes de cambiar los datos. Si el cambio no coincide con los criterios, se muestra una excepción que contiene el texto de [GetValidationText.](#getvalidationtext)

La validación solo se admite para las bases de datos que utilizan el motor de base de datos Microsoft Jet. La expresión no puede hacer referencia a funciones definidas por el usuario, funciones de agregado de dominio, funciones de agregado SQL o consultas. Una regla de `CDaoTableDef` validación para un objeto puede hacer referencia a varios campos de ese objeto.

Por ejemplo, para los campos denominados *hire_date* y *termination_date*, una regla de validación podría ser:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.

## <a name="cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a>CDaoTableDef::SetValidationText

Llame a esta función miembro para establecer `CDaoTableDef` el texto de excepción de una regla de validación para un objeto con una tabla base subyacente compatible con el motor de base de datos de Microsoft Jet.

```cpp
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parámetros

*lpszValidationText*<br/>
Un puntero a una expresión de cadena que especifica el texto que se muestra si se introducen datos no es válido.

### <a name="remarks"></a>Observaciones

No se puede establecer el texto de validación de una tabla adjunta.

Para obtener información relacionada, vea el tema "Propiedad ValidationText" en la Ayuda de DAO.

## <a name="see-also"></a>Vea también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)<br/>
[Clase CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
