---
title: Clase CDaoTableDef | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoTableDef
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], DAO
- tabledefs [C++]
- CDaoTableDef class
- database tables [C++], attached table definition
- database tables [C++], base table definition
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8bfd0ef3c63c243cabb0a4f841ba278fbeed4ae8
ms.lasthandoff: 02/24/2017

---
# <a name="cdaotabledef-class"></a>Clase CDaoTableDef
Representa la definición almacenada de una tabla base o una tabla asociada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDaoTableDef : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Construye un **CDaoTableDef** objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoTableDef:: Append](#append)|Agrega una nueva tabla a la base de datos.|  
|[CDaoTableDef:: CanUpdate](#canupdate)|Devuelve cero si se puede actualizar la tabla (puede modificar la definición de campos o propiedades de la tabla).|  
|[CDaoTableDef::Close](#close)|Cierra un objeto tabledef abierto.|  
|[CDaoTableDef:: Create](#create)|Crea una tabla que se puede agregar a la base de datos mediante [anexado](#append).|  
|[CDaoTableDef:: CreateField](#createfield)|Se llama para crear un campo de una tabla.|  
|[CDaoTableDef::CreateIndex](#createindex)|Se llama para crear un índice para una tabla.|  
|[CDaoTableDef::DeleteField](#deletefield)|Se llama para eliminar un campo de una tabla.|  
|[CDaoTableDef::DeleteIndex](#deleteindex)|Se llama para eliminar un índice de una tabla.|  
|[CDaoTableDef::GetAttributes](#getattributes)|Devuelve un valor que indica una o varias características de un `CDaoTableDef` objeto.|  
|[CDaoTableDef::GetConnect](#getconnect)|Devuelve un valor que proporciona información sobre el origen de una tabla.|  
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Devuelve la fecha y hora de la tabla base subyacente un `CDaoTableDef` se creó el objeto.|  
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Devuelve la fecha y hora del cambio más reciente realizado en el diseño de la tabla base.|  
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Devuelve un valor que representa el número de campos de la tabla.|  
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Devuelve los tipos específicos de información sobre los campos en la tabla.|  
|[CDaoTableDef::GetIndexCount](#getindexcount)|Devuelve el número de índices de la tabla.|  
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Devuelve los tipos específicos de información acerca de los índices de la tabla.|  
|[CDaoTableDef::GetName](#getname)|Devuelve el nombre definido por el usuario de la tabla.|  
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Devuelve el número de registros de la tabla.|  
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Devuelve un valor que especifica el nombre de la tabla asociada en la base de datos de origen.|  
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Devuelve un valor que valida los datos de un campo cuando se cambia o se agrega a una tabla.|  
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Devuelve un valor que especifica el texto del mensaje que su aplicación muestra si el valor de un objeto Field no cumple la regla de validación especificado.|  
|[CDaoTableDef::IsOpen](#isopen)|Devuelve cero si la tabla está abierto.|  
|[CDaoTableDef::Open](#open)|Se abre una definición de tabla existente almacenado en la base de datos 's colección de definición de tabla.|  
|[CDaoTableDef:: RefreshLink](#refreshlink)|Actualiza la información de conexión para una tabla asociada.|  
|[CDaoTableDef::SetAttributes](#setattributes)|Establece un valor que indica una o varias características de un `CDaoTableDef` objeto.|  
|[CDaoTableDef::SetConnect](#setconnect)|Establece un valor que proporciona información sobre el origen de una tabla.|  
|[CDaoTableDef::SetName](#setname)|Establece el nombre de la tabla.|  
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Establece un valor que especifica el nombre de una tabla asociada en la base de datos de origen.|  
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Establece un valor que valida los datos de un campo cuando se cambia o se agrega a una tabla.|  
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Establece un valor que especifica el texto del mensaje que su aplicación muestra si el valor de un objeto Field no cumple la regla de validación especificado.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Puntero a la interfaz DAO subyacente al objeto de definición de tabla.|  
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Base de datos de origen para esta tabla.|  
  
## <a name="remarks"></a>Comentarios  
 Cada objeto de base de datos DAO mantiene una colección, denominada definiciones de tabla, que contiene todos los objetos de definición de tabla DAO guardados.  
  
 Manipular una definición de tabla mediante una `CDaoTableDef` objeto. Por ejemplo, se puede:  
  
-   Examinar la estructura de campos e índices de cualquier tabla local, adjunta o externa en una base de datos.  
  
-   Llame a la `SetConnect` y `SetSourceTableName` funciones miembro para tablas asociadas y use el `RefreshLink` función miembro para actualizar las conexiones a tablas asociadas.  
  
-   Llame a la `CanUpdate` para determinar si puede editar las definiciones de campo en la tabla de función miembro.  
  
-   Obtener o establecer condiciones de validación mediante el `GetValidationRule` y `SetValidationRule`y el `GetValidationText` y `SetValidationText` funciones miembro.  
  
-   Utilice la **abiertos** función de miembro para crear una tabla, Dynaset o tipo snapshot `CDaoRecordset` objeto.  
  
    > [!NOTE]
    >  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Puede seguir acceso a orígenes de datos ODBC con las clases DAO; Generalmente, las clases DAO ofrecen capacidades de superior porque son específicas para el motor de base de datos Microsoft Jet.  
  
### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Usar objetos de definición de tabla para trabajar con una tabla existente o crear una nueva tabla  
  
1.  En todos los casos, construir una `CDaoTableDef` objeto, proporcionando un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) del objeto al que pertenece la tabla.  
  
2.  A continuación, haga lo siguiente, según lo que desee:  
  
    -   Para utilizar un guardado de tabla existente, llame al objeto de definición de tabla [abiertos](#open) función miembro, proporcionando el nombre de la tabla guardada.  
  
    -   Para crear una nueva tabla, llame al objeto de definición de tabla [crear](#create) función miembro, proporcionando el nombre de la tabla. Llame a [CreateField](#createfield) y [CreateIndex](#createindex) para agregar campos y los índices para la tabla.  
  
    -   Llame a [anexado](#append) para guardar la tabla, ésta se agrega a la colección de definiciones de tabla de la base de datos. **Crear** coloca la definición de tabla en un estado abierto, es así después de llamar a **crear** no se llama **abrir**.  
  
        > [!TIP]
        >  Es la manera más fácil de crear tablas guardadas crearlos y almacenarlos en la base de datos mediante Microsoft Access. A continuación, puede abrir y utilizarlos en el código MFC.  
  
 Para utilizar el objeto de definición de tabla se abrió o creó, crear y abrir un `CDaoRecordset` objeto, especificando el nombre de la definición de tabla con un **dbOpenTable** valor en el `nOpenType` parámetro.  
  
 Usar un objeto de definición de tabla para crear un `CDaoRecordset` de objeto, se suelen crear o abre una definición de tabla, como se describió anteriormente, construir un objeto de conjunto de registros, pasando un puntero al objeto de definición de tabla al llamar a [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). Pasa la definición de tabla debe estar en un estado abierto. Para obtener más información, vea la clase [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Cuando termine de utilizar un objeto de definición de tabla, llame a su [cerrar](../../mfc/reference/cdaorecordset-class.md#close) miembro de función; a continuación, destruya el objeto de definición de tabla.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoTableDef`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
##  <a name="a-nameappenda--cdaotabledefappend"></a><a name="append"></a>CDaoTableDef:: Append  
 Llame a esta función miembro después de llamar a [crear](#create) para crear un nuevo objeto de definición de tabla para guardar la definición de tabla en la base de datos.  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Comentarios  
 La función agrega el objeto a la colección de definiciones de tabla de la base de datos. Puede usar la definición de tabla como un objeto temporal al definir anexando No, pero si desea guardar y usarlo, debe llamar a **anexado**.  
  
> [!NOTE]
>  Si intenta agregar una definición de tabla sin nombre (que contiene una cadena nula o vacía), MFC inicia una excepción.  
  
 Para obtener información relacionada, vea el tema "Método Append" en la Ayuda de DAO.  
  
##  <a name="a-namecanupdatea--cdaotabledefcanupdate"></a><a name="canupdate"></a>CDaoTableDef:: CanUpdate  
 Llame a esta función miembro para determinar si la definición de la tabla subyacente un `CDaoTableDef` se puede cambiar el objeto.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se puede modificar la estructura de tabla (esquema) (Agregar o eliminar campos e índices), de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, una tabla recién creada subyacente un `CDaoTableDef` se puede actualizar el objeto y una tabla asociada subyacente un `CDaoTableDef` no se puede actualizar el objeto. Un `CDaoTableDef` objeto puede ser actualizable, incluso si el objeto recordset resultante no es actualizable.  
  
 Para obtener información relacionada, vea el tema "Propiedad actualizable" en la Ayuda de DAO.  
  
##  <a name="a-namecdaotabledefa--cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef  
 Construye un **CDaoTableDef** objeto.  
  
```  
CDaoTableDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDatabase`  
 Un puntero a un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Después de crear el objeto, se debe llamar a la [crear](#create) o [abiertos](#open) función miembro. Cuando termine con el objeto, debe llamar a su [cerrar](#close) miembro de función y destruir el `CDaoTableDef` objeto.  
  
##  <a name="a-nameclosea--cdaotabledefclose"></a><a name="close"></a>CDaoTableDef::Close  
 Llame a esta función miembro para cerrar y liberar el objeto de definición de tabla.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente después de llamar a **cerrar**, eliminar el objeto de definición de tabla si se asignó con **nueva**.  
  
 Puede llamar a [abiertos](#open) nuevo después de llamar a **cerrar**. Esto le permite volver a utilizar el objeto de definición de tabla.  
  
 Para obtener información relacionada, vea el tema "Método Close" en la Ayuda de DAO.  
  
##  <a name="a-namecreatea--cdaotabledefcreate"></a><a name="create"></a>CDaoTableDef:: Create  
 Llame a esta función miembro para crear una nueva tabla guardada.  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    long lAttributes = 0,  
    LPCTSTR lpszSrcTable = NULL,  
    LPCTSTR lpszConnect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Un puntero a una cadena que contiene el nombre de la tabla.  
  
 `lAttributes`  
 Un valor correspondiente a las características de la tabla representada por el objeto de definición de tabla. Puede usar la operación bit a bit OR para combinar cualquiera de las siguientes constantes:  
  
|Constante|Descripción|  
|--------------|-----------------|  
|**dbAttachExclusive**|Bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que la tabla es una tabla asociada abierta para su uso exclusivo.|  
|**dbAttachSavePWD**|Bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que el identificador de usuario y la contraseña para la tabla asociada se guardan con la información de conexión.|  
|**dbSystemObject**|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet.|  
|**dbHiddenObject**|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet.|  
  
 *lpszSrcTable*  
 Un puntero a una cadena que contiene el nombre de la tabla de origen. De forma predeterminada, este valor se inicializa como **NULL**.  
  
 `lpszConnect`  
 Puntero a una cadena que contiene la cadena de conexión predeterminada. De forma predeterminada, este valor se inicializa como **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Una vez con el nombre de la definición de tabla, puede llamar [anexado](#append) para guardar la definición de tabla en la colección de definiciones de tabla de la base de datos. Después de llamar a **anexado**, la definición de tabla está en un estado abierto y se puede utilizar para crear un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto.  
  
 Para obtener información relacionada, vea el tema "Método CreateTableDef" en la Ayuda de DAO.  
  
##  <a name="a-namecreatefielda--cdaotabledefcreatefield"></a><a name="createfield"></a>CDaoTableDef:: CreateField  
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
 `lpszName`  
 Puntero a una expresión de cadena que especifica el nombre de este campo.  
  
 `nType`  
 Un valor que indica el tipo de datos del campo. El valor puede ser uno de estos valores:  
  
|Tipo|Tamaño (bytes)|Descripción|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 byte|BOOL|  
|**dbByte**|1|BYTE|  
|**dbInteger**|2|int|  
|**dbLong**|4|long|  
|**dbCurrency**|8|Moneda ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|flotante|  
|**dbDouble**|8|double|  
|**dbDate**|8|Fecha y hora ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 – 255|Texto ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|Binarios largos (objeto OLE), [CLongBinary](../../mfc/reference/clongbinary-class.md) o [CByteArray](../../mfc/reference/cbytearray-class.md)|  
|**dbMemo**|0|Memorando ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
  
 `lSize`  
 Un valor que indica el tamaño máximo, en bytes, de un campo que contiene el texto, o el tamaño de un campo que contiene valores numéricos o de texto fijo. El `lSize` parámetro se omite para todos los campos de texto salvo.  
  
 `lAttributes`  
 Un valor que corresponde a las características del campo y se puede combinar con un OR bit a bit.  
  
|Constante|Descripción|  
|--------------|-----------------|  
|**dbFixedField**|El tamaño del campo es fijo (valor predeterminado para los campos numéricos).|  
|**dbVariableField**|El tamaño del campo es variable (sólo campos de texto).|  
|**dbAutoIncrField**|El valor del campo para nuevos registros se incrementa automáticamente en un entero largo único que no se puede cambiar. Solo se admite para las tablas de base de datos Microsoft Jet.|  
|**dbUpdatableField**|Se puede cambiar el valor del campo.|  
|**dbDescending**|El campo se ordena en orden descendente (Z-A o 0 – 100) pedido (sólo se aplica a un objeto Field de una colección de campos de un objeto de índice). Si se omite esta constante, el campo se ordena en orden ascendente (A – Z o 0 – 100) pedido (valor predeterminado).|  
  
 `fieldinfo`  
 Una referencia a un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura.  
  
### <a name="remarks"></a>Comentarios  
 Un **DAOField** objeto (OLE) se crea y se anexa a la colección de campos de la **DAOTableDef** objeto (OLE). Además de su uso para examinar las propiedades de objeto, también puede utilizar `CDaoFieldInfo` para construir un parámetro de entrada para la creación de nuevos campos en una definición de tabla. La primera versión de `CreateField` es más fácil de usar, pero si desea un control más preciso, puede utilizar la segunda versión de `CreateField`, que toma un `CDaoFieldInfo` parámetro.  
  
 Si utiliza la versión de `CreateField` que toma un `CDaoFieldInfo` parámetro, debe cuidadosamente establecer cada uno de los siguientes miembros de la `CDaoFieldInfo` estructura:  
  
- **m_strName**  
  
- `m_nType`  
  
- **m_lSize**  
  
- **m_lAttributes**  
  
- **m_bAllowZeroLength**  
  
 Los restantes miembros del `CDaoFieldInfo` debe establecerse en **0**, **FALSE**, o una cadena vacía, según corresponda para el miembro, o un `CDaoException` puede producirse.  
  
 Para obtener información relacionada, vea el tema "Método CreateField" en la Ayuda de DAO.  
  
##  <a name="a-namecreateindexa--cdaotabledefcreateindex"></a><a name="createindex"></a>CDaoTableDef::CreateIndex  
 Llame a esta función para agregar un índice a una tabla.  
  
```  
void CreateIndex(CDaoIndexInfo& indexinfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `indexinfo`  
 Una referencia a un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura.  
  
### <a name="remarks"></a>Comentarios  
 Índices especifican el orden de registros que se tiene acceso desde las tablas de base de datos y si no se aceptan los registros duplicados. Los índices también proporcionan un acceso eficaz a los datos.  
  
 No tiene que crear índices para las tablas, pero en tablas grandes y sin indizadas, el acceso a un registro determinado o crear un conjunto de registros puede tardar mucho tiempo. Por otro lado, crear demasiados índices ralentiza el actualizar, anexar y eliminar operaciones como todos los índices se actualizan automáticamente. Tenga en cuenta estos factores cuando decida qué índices se deben crear.  
  
 Los siguientes miembros de la `CDaoIndexInfo` se debe establecer la estructura:  
  
- **m_strName** se debe proporcionar un nombre.  
  
- `m_pFieldInfos`Debe apuntar a una matriz de `CDaoIndexFieldInfo` estructuras.  
  
- `m_nFields`Debe especificar el número de campos de la matriz de `CDaoFieldInfo` estructuras.  
  
 Los restantes miembros se omite si establecerá en **FALSE**. Además, el **m_lDistinctCount** miembro se omite durante la creación del índice.  
  
##  <a name="a-namedeletefielda--cdaotabledefdeletefield"></a><a name="deletefield"></a>CDaoTableDef::DeleteField  
 Llame a esta función miembro para quitar un campo y hacerla accesible.  
  
```  
void DeleteField(LPCTSTR lpszName);  
void DeleteField(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Puntero a una expresión de cadena que es el nombre de un campo existente.  
  
 `nIndex`  
 El índice del campo en la colección de campos basada en cero de la tabla, para la búsqueda por índice.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar esta función miembro en un objeto nuevo que no se ha anexado a la base de datos o cuando [CanUpdate](#canupdate) devuelve distinto de cero.  
  
 Para obtener información relacionada, vea el tema "Método Delete" en la Ayuda de DAO.  
  
##  <a name="a-namedeleteindexa--cdaotabledefdeleteindex"></a><a name="deleteindex"></a>CDaoTableDef::DeleteIndex  
 Llame a esta función miembro para eliminar un índice en una tabla subyacente.  
  
```  
void DeleteIndex(LPCTSTR lpszName);  
void DeleteIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Puntero a una expresión de cadena que es el nombre de un índice existente.  
  
 `nIndex`  
 El índice de matriz del objeto de índice en basado en cero TableDefs (colección la base de datos), para la búsqueda por índice.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar esta función miembro en un objeto nuevo que no se ha anexado a la base de datos o cuando [CanUpdate](#canupdate) devuelve distinto de cero.  
  
 Para obtener información relacionada, vea el tema "Método Delete" en la Ayuda de DAO.  
  
##  <a name="a-namegetattributesa--cdaotabledefgetattributes"></a><a name="getattributes"></a>CDaoTableDef::GetAttributes  
 Para una `CDaoTableDef` objeto, el valor devuelto especifica las características de la tabla representada por el `CDaoTableDef` de objetos y puede ser la suma de estas constantes:  
  
```  
long GetAttributes();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor que indica una o varias características de un `CDaoTableDef` objeto.  
  
### <a name="remarks"></a>Comentarios  
  
|Constante|Descripción|  
|--------------|-----------------|  
|**dbAttachExclusive**|Bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que la tabla es una tabla asociada abierta para su uso exclusivo.|  
|**dbAttachSavePWD**|Bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que el identificador de usuario y la contraseña para la tabla asociada se guardan con la información de conexión.|  
|**dbSystemObject**|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet.|  
|**dbHiddenObject**|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet.|  
|**dbAttachedTable**|Indica que la tabla es una tabla de una base de datos no son ODBC, como una base de datos de Paradox asociada.|  
|**dbAttachedODBC**|Indica que la tabla es una tabla de una base de datos ODBC, como Microsoft SQL Server asociada.|  
  
 Una tabla del sistema es una tabla creada por el motor de base de datos de Microsoft Jet que contiene diversa información interna.  
  
 Una tabla oculta es una tabla creada para el uso temporal por el motor de base de datos Microsoft Jet.  
  
 Para obtener información relacionada, vea el tema "Propiedad Attributes" en la Ayuda de DAO.  
  
##  <a name="a-namegetconnecta--cdaotabledefgetconnect"></a><a name="getconnect"></a>CDaoTableDef::GetConnect  
 Llame a esta función miembro para obtener la cadena de conexión para un origen de datos.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que contiene el tipo de ruta de acceso y la base de datos para la tabla.  
  
### <a name="remarks"></a>Comentarios  
 Para una `CDaoTableDef` objeto que representa una tabla asociada, la `CString` objeto consta de una o dos partes (un especificador de tipo de base de datos y una ruta de acceso a la base de datos).  
  
 La ruta de acceso, como se muestra en la tabla siguiente es la ruta de acceso completa al directorio que contiene los archivos de base de datos y debe ir precedido por el identificador "base de datos =". En algunos casos (como bases de datos con Microsoft Jet y Microsoft Excel), un nombre de archivo específico se incluye en el argumento de ruta de acceso de la base de datos.  
  
 La tabla de [CDaoTableDef::SetConnect](#setconnect) muestra los tipos posibles de la base de datos y sus correspondientes especificadores y rutas de acceso:  
  
 Para las tablas de base de base de datos Microsoft Jet, el especificador es una cadena vacía ("").  
  
 Si se requiere una contraseña, pero no se proporciona, el controlador ODBC muestra un inicio de sesión cuadro de diálogo la primera vez que se tiene acceso a una tabla y, de nuevo si la conexión se cierra y se vuelve a abrir. Si tiene una tabla asociada la **dbAttachSavePWD** atributo, el símbolo del sistema de inicio de sesión no aparecerá cuando se vuelve a abrir la tabla.  
  
 Para obtener información relacionada, vea el tema "Propiedad conectarse" en la Ayuda de DAO.  
  
##  <a name="a-namegetdatecreateda--cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a>CDaoTableDef::GetDateCreated  
 Llame a esta función para determinar la fecha y hora de la tabla subyacente del `CDaoTableDef` se creó el objeto.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que contiene la fecha y hora de la creación de la tabla subyacente del `CDaoTableDef` objeto.  
  
### <a name="remarks"></a>Comentarios  
 La configuración de fecha y hora se deriva del equipo en el que se creó la tabla base o se actualizó por última vez. En un entorno multiusuario, los usuarios deben obtener estos valores directamente desde el servidor de archivos para evitar discrepancias; es decir, todos los clientes deben usar un origen de hora "estándar", quizás de un servidor.  
  
 Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
##  <a name="a-namegetdatelastupdateda--cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated  
 Llame a esta función para determinar la fecha y hora de la tabla subyacente del **CDaoTableDef** se actualizó por última vez el objeto.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que contiene la fecha y hora de la tabla subyacente del **CDaoTableDef** se actualizó por última vez el objeto.  
  
### <a name="remarks"></a>Comentarios  
 La configuración de fecha y hora se deriva del equipo en el que se creó la tabla base o se actualizó por última vez. En un entorno multiusuario, los usuarios deben obtener estos valores directamente desde el servidor de archivos para evitar discrepancias; es decir, todos los clientes deben usar un origen de hora "estándar", quizás de un servidor.  
  
 Para obtener información relacionada, vea el tema "DateCreated y LastUpdated propiedades" en la Ayuda de DAO.  
  
##  <a name="a-namegetfieldcounta--cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a>CDaoTableDef::GetFieldCount  
 Llame a esta función miembro para recuperar el número de campos definidos en la tabla.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de campos de la tabla.  
  
### <a name="remarks"></a>Comentarios  
 Si su valor es 0, no hay ningún objeto en la colección.  
  
 Para obtener información relacionada, vea el tema "Propiedad Count" en la Ayuda de DAO.  
  
##  <a name="a-namegetfieldinfoa--cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo  
 Llame a esta función miembro para obtener información acerca de un campo definido en la definición de tabla de diferentes tipos.  
  
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
 `nIndex`  
 El índice del objeto field en la colección de campos basada en cero de la tabla, para la búsqueda por índice.  
  
 `fieldinfo`  
 Una referencia a un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información sobre el campo que desea recuperar. Las opciones disponibles se muestran aquí junto con lo que hacen que la función devuelva:  
  
- `AFX_DAO_PRIMARY_INFO`(Valor predeterminado) Nombre, tipo, tamaño, atributos. Utilice esta opción para mejorar el rendimiento.  
  
- `AFX_DAO_SECONDARY_INFO`La información principal, además de: posición Ordinal, necesaria, permitir cero tabla de origen de longitud, orden de intercalación, nombre externa, el campo de origen  
  
- `AFX_DAO_ALL_INFO`Información primaria y secundaria, además de: valor predeterminado de la regla de validación, texto de validación  
  
 `lpszName`  
 Un puntero al nombre del objeto de campo para la búsqueda por nombre. El nombre es una cadena con un máximo de 64 caracteres que identifica inequívocamente el campo.  
  
### <a name="remarks"></a>Comentarios  
 Una versión de la función le permite buscar un campo por su índice. La otra versión le permite buscar un campo por su nombre.  
  
 Para obtener una descripción de la información devuelta, consulte el [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de `dwInfoOptions`. Cuando se solicita información de un nivel, obtendrá información de los niveles anteriores también.  
  
 Para obtener información relacionada, vea el tema "Propiedad Attributes" en la Ayuda de DAO.  
  
##  <a name="a-namegetindexcounta--cdaotabledefgetindexcount"></a><a name="getindexcount"></a>CDaoTableDef::GetIndexCount  
 Llame a esta función miembro para obtener el número de índices de una tabla.  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de índices de la tabla.  
  
### <a name="remarks"></a>Comentarios  
 Si su valor es 0, no hay ningún índice en la colección.  
  
 Para obtener información relacionada, vea el tema "Propiedad Count" en la Ayuda de DAO.  
  
##  <a name="a-namegetindexinfoa--cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo  
 Llame a esta función miembro para obtener información acerca de un índice definido en la definición de tabla de diferentes tipos.  
  
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
 `nIndex`  
 Índice numérico del objeto de índice en la colección de índices basada en cero de la tabla, para la búsqueda por su posición en la colección.  
  
 `indexinfo`  
 Una referencia a un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura.  
  
 `dwInfoOptions`  
 Opciones que especifican qué información sobre el índice para recuperar. Las opciones disponibles se muestran aquí junto con lo que hacen que la función devuelva:  
  
- `AFX_DAO_PRIMARY_INFO`Campos de nombre, información de campo. Utilice esta opción para mejorar el rendimiento.  
  
- `AFX_DAO_SECONDARY_INFO`La información principal, además de: principal, Unique, Clustered, omitir valores nulos, necesarias, externa  
  
- `AFX_DAO_ALL_INFO`Información primaria y secundaria, además de: Distinct Count  
  
 `lpszName`  
 Puntero al nombre del objeto de índice para la búsqueda por nombre.  
  
### <a name="remarks"></a>Comentarios  
 Una versión de la función le permite buscar un índice por su posición en la colección. La otra versión le permite buscar un índice por nombre.  
  
 Para obtener una descripción de la información devuelta, consulte el [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) estructura. Esta estructura no tiene miembros que corresponden a los elementos de información enumerados anteriormente en la descripción de `dwInfoOptions`. Cuando se solicita información de un nivel, obtendrá información de los niveles anteriores también.  
  
 Para obtener información relacionada, vea el tema "Propiedad Attributes" en la Ayuda de DAO.  
  
##  <a name="a-namegetnamea--cdaotabledefgetname"></a><a name="getname"></a>CDaoTableDef::GetName  
 Llame a esta función miembro para obtener el nombre definido por el usuario de la tabla subyacente.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un nombre definido por el usuario para una tabla.  
  
### <a name="remarks"></a>Comentarios  
 Este nombre empieza por una letra y puede contener un máximo de 64 caracteres. Puede incluir números y caracteres de subrayado, pero no puede incluir signos de puntuación o espacios.  
  
 Para obtener información relacionada, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
##  <a name="a-namegetrecordcounta--cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a>CDaoTableDef::GetRecordCount  
 Llame a esta función miembro para averiguar el número de registros en una `CDaoTableDef` objeto.  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de registros que se obtiene acceso en un objeto de definición de tabla.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a `GetRecordCount` para un tipo de tabla `CDaoTableDef` objeto refleja el número aproximado de registros de la tabla y se ve afectada inmediatamente cuando se agregan o eliminan registros de la tabla. Deshace las transacciones aparecerán como parte del número de registros hasta que se llama [CDaoWorkspace:: CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). Un `CDaoTableDef` objeto sin registros tiene un valor de propiedad de recuento de registros de 0. Al trabajar con tablas adjuntas o bases de datos ODBC, `GetRecordCount` siempre devuelve –&1;.  
  
 Para obtener información relacionada, vea el tema "Propiedad RecordCount" en la Ayuda de DAO.  
  
##  <a name="a-namegetsourcetablenamea--cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName  
 Llame a esta función miembro para recuperar el nombre de una tabla asociada en una base de datos de origen.  
  
```  
CString GetSourceTableName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que especifica el nombre de origen de una tabla asociada, o una cadena vacía si una tabla de datos nativos.  
  
### <a name="remarks"></a>Comentarios  
 Una tabla asociada es una tabla en otra base de datos vinculada a una base de datos Microsoft Jet. Datos de las tablas asociadas permanecen en la base de datos externa, donde se pueden manipular mediante otras aplicaciones.  
  
 Para obtener información relacionada, vea el tema "Propiedad SourceTableName" en la Ayuda de DAO.  
  
##  <a name="a-namegetvalidationrulea--cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule  
 Llame a esta función miembro para recuperar la regla de validación para una definición de tabla.  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **CString** objeto que valida los datos de un campo cuando se cambia o se agrega a una tabla.  
  
### <a name="remarks"></a>Comentarios  
 Las reglas de validación se utilizan en relación con las operaciones de actualización. Si una definición de tabla contiene una regla de validación, las actualizaciones de la definición de esa tabla deben coincidir con los criterios predeterminados antes de cambian los datos. Si el cambio no coincide con los criterios, una excepción que contiene el valor de [GetValidationText](#getvalidationtext) se produce. Para una `CDaoTableDef` objeto esto `CString` es de sólo lectura para una tabla asociada y la lectura y escritura para una tabla base.  
  
 Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.  
  
##  <a name="a-namegetvalidationtexta--cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoTableDef::GetValidationText  
 Llame a esta función para recuperar la cadena que se muestra cuando un usuario escribe datos que no coincide con la regla de validación.  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que especifica el texto que se muestra si el usuario escribe datos que no coincide con la regla de validación.  
  
### <a name="remarks"></a>Comentarios  
 Para una `CDaoTableDef` objeto esto `CString` es de sólo lectura para una tabla asociada y la lectura y escritura para una tabla base.  
  
 Para obtener información relacionada, vea el tema "Propiedad texto de validación" en la Ayuda de DAO.  
  
##  <a name="a-nameisopena--cdaotabledefisopen"></a><a name="isopen"></a>CDaoTableDef::IsOpen  
 Llame a esta función miembro para determinar si la `CDaoTableDef` objeto está abierto.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CDaoTableDef` objeto es abierto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namempdatabasea--cdaotabledefmpdatabase"></a><a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase  
 Contiene un puntero a la [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto para esta tabla.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namempdaotabledefa--cdaotabledefmpdaotabledef"></a><a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef  
 Contiene un puntero a la interfaz OLE para el objeto DAO tabledef subyacente la `CDaoTableDef` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este puntero si necesita tener acceso directamente a la interfaz DAO.  
  
##  <a name="a-nameopena--cdaotabledefopen"></a><a name="open"></a>CDaoTableDef::Open  
 Llamada esta función miembro para abrir una definición de tabla guardada previamente en la base de datos del conjunto de definición de tabla.  
  
```  
virtual void Open(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Puntero a una cadena que especifica un nombre de tabla.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namerefreshlinka--cdaotabledefrefreshlink"></a><a name="refreshlink"></a>CDaoTableDef:: RefreshLink  
 Llame a esta función miembro para actualizar la información de conexión para una tabla asociada.  
  
```  
void RefreshLink();
```  
  
### <a name="remarks"></a>Comentarios  
 Cambiar la información de conexión para una tabla asociada llamando a [SetConnect](#setconnect) correspondiente `CDaoTableDef` objeto y, a continuación, usar el `RefreshLink` para actualizar la información de función miembro. Cuando se llama a `RefreshLink`, no se cambian las propiedades de la tabla adjunto.  
  
 Para forzar modificado información de conexión para que surta efecto, todos los [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) deben cerrarse objetos en función de esta definición de tabla.  
  
 Para obtener información relacionada, vea el tema "Método RefreshLink" en la Ayuda de DAO.  
  
##  <a name="a-namesetattributesa--cdaotabledefsetattributes"></a><a name="setattributes"></a>CDaoTableDef::SetAttributes  
 Establece un valor que indica una o varias características de un `CDaoTableDef` objeto.  
  
```  
void SetAttributes(long lAttributes);
```  
  
### <a name="parameters"></a>Parámetros  
 `lAttributes`  
 Características de la tabla representada por el `CDaoTableDef` de objetos y puede ser la suma de estas constantes:  
  
|Constante|Descripción|  
|--------------|-----------------|  
|**dbAttachExclusive**|Bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que la tabla es una tabla asociada abierta para su uso exclusivo.|  
|**dbAttachSavePWD**|Bases de datos que utilizan el motor de base de datos Microsoft Jet, indica que el identificador de usuario y la contraseña para la tabla asociada se guardan con la información de conexión.|  
|**dbSystemObject**|Indica que la tabla es una tabla del sistema proporcionada por el motor de base de datos Microsoft Jet.|  
|**dbHiddenObject**|Indica que la tabla es una tabla oculta proporcionada por el motor de base de datos Microsoft Jet.|  
  
### <a name="remarks"></a>Comentarios  
 Al establecer varios atributos, se puede combinar sumando las constantes adecuadas mediante el operador OR bit a bit. Configuración de **dbAttachExclusive** en una tabla no asociada produce una excepción. La combinación de los siguientes valores también generan una excepción:  
  
- **dbAttachExclusive | dbAttachedODBC**  
  
- **dbAttachSavePWD | dbAttachedTable**  
  
 Para obtener información relacionada, vea el tema "Propiedad Attributes" en la Ayuda de DAO.  
  
##  <a name="a-namesetconnecta--cdaotabledefsetconnect"></a><a name="setconnect"></a>CDaoTableDef::SetConnect  
 Para una `CDaoTableDef` objeto que representa una tabla asociada, el objeto de cadena consta de una o dos partes (un especificador de tipo de base de datos y una ruta de acceso a la base de datos).  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszConnect`  
 Puntero a una expresión de cadena que especifica parámetros adicionales para pasar a ODBC o controladores ISAM instalables.  
  
### <a name="remarks"></a>Comentarios  
 La ruta de acceso, como se muestra en la tabla siguiente es la ruta de acceso completa al directorio que contiene los archivos de base de datos y debe ir precedido por el identificador "base de datos =". En algunos casos (como bases de datos con Microsoft Jet y Microsoft Excel), un nombre de archivo específico se incluye en el argumento de ruta de acceso de la base de datos.  
  
> [!NOTE]
>  No incluya espacios en blanco alrededor del signo igual en las instrucciones de la ruta de acceso de la forma "base de datos = unidad:\\\path". Esto producirá una excepción y el error de conexión.  
  
 La siguiente tabla muestra los tipos posibles de la base de datos y sus correspondientes especificadores y rutas de acceso:  
  
|Tipo de base de datos|Especificador|Ruta de acceso|  
|-------------------|---------------|----------|  
|Base de datos mediante el motor de base de datos de Jet|"[ `database`];"|" `drive`:\\\ *path*\\\ *filename*. MDB"|  
|dBASE III|"dBASE III;"|" `drive`:\\\ *path*"|  
|dBASE IV|"dBASE IV;"|" `drive`:\\\ *path*"|  
|dBASE 5|"dBASE 5.0;"|" `drive`:\\\ *path*"|  
|Paradox 3.x|"Paradox 3.x;"|" `drive`:\\\ *path*"|  
|Paradox 4.x|"Paradox 4.x;"|" `drive`:\\\ *path*"|  
|Paradox 5.x|"Paradox 5.x;"|" `drive`:\\\ *path*"|  
|Excel 3.0|"Excel 3.0";|" `drive`:\\\ *path*\\\ *filename*. XLS"|  
|Excel 4.0|"Excel 4.0";|" `drive`:\\\ *path*\\\ *filename*. XLS"|  
|Excel 5.0 o Excel 95|"Excel 5.0;"|" `drive`:\\\ *path*\\\ *filename*. XLS"|  
|Excel 97|"Excel 8.0;"|" `drive`:\\\ *path*\ *filename*. XLS"|  
|Importación de HTML|"Importar HTML;"|" `drive`:\\\ *path*\ *filename*"|  
|Exportación de HTML|"Exportar HTML;"|" `drive`:\\\ *path*"|  
|Texto|"Texto";|"unidad:\\\path"|  
|ODBC|"ODBC; Base de datos = `database`; UID= *user*; PWD = *contraseña*; DSN = *datasourcename;* LOGINTIMEOUT = *segundos;*" (Esto puede no ser una cadena de conexión completa para todos los servidores; es sólo un ejemplo. Es muy importante no tener espacios entre los parámetros.)|Ninguna|  
|Exchange|"Exchange;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE = {0 | 1};]<br /><br /> [Perfil = *perfiles*;]<br /><br /> [PWD = *contraseña*;]<br /><br /> [BASE DE DATOS = `database`;] "|*"drive*:\\\ *path*\\\ *filename*. MDB"|  
  
> [!NOTE]
>  Btrieve ya no se admite a partir de DAO 3.5.  
  
 Debe utilizar una barra diagonal inversa doble (\\\\) en las cadenas de conexión. Si ha modificado las propiedades de una conexión existente con `SetConnect`, se debe llamar posteriormente a [RefreshLink](#refreshlink). Si se inicializan las propiedades de conexión mediante `SetConnect`, necesita no llamada `RefreshLink`, pero si decide hacerlo, agregue primero la definición de tabla.  
  
 Si se requiere una contraseña, pero no se proporciona, el controlador ODBC muestra un inicio de sesión cuadro de diálogo la primera vez que se tiene acceso a una tabla y, de nuevo si la conexión se cierra y se vuelve a abrir.  
  
 Puede establecer la cadena de conexión para una `CDaoTableDef` objeto para proporcionar un argumento de origen a la **crear** función miembro. Puede comprobar la configuración para determinar el tipo, la ruta de acceso, la Id. de usuario, la contraseña o el origen de datos de la base de datos. Para obtener más información, consulte la documentación para el controlador específico.  
  
 Para obtener información relacionada, vea el tema "Propiedad conectarse" en la Ayuda de DAO.  
  
##  <a name="a-namesetnamea--cdaotabledefsetname"></a><a name="setname"></a>CDaoTableDef::SetName  
 Llame a esta función miembro para establecer un nombre definido por el usuario para una tabla.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Puntero a una expresión de cadena que especifica un nombre de una tabla.  
  
### <a name="remarks"></a>Comentarios  
 El nombre debe empezar por una letra y puede contener un máximo de 64 caracteres. Puede incluir números y caracteres de subrayado, pero no puede incluir signos de puntuación o espacios.  
  
 Para obtener información relacionada, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
##  <a name="a-namesetsourcetablenamea--cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName  
 Llame a esta función miembro para especificar el nombre de una tabla asociada o el nombre de la tabla base en el que el `CDaoTableDef` se basa el objeto, tal y como existe en el origen de los datos.  
  
```  
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszSrcTableName*  
 Puntero a una expresión de cadena que especifica un nombre de tabla en la base de datos externo. Para una tabla base, el valor es una cadena vacía ("").  
  
### <a name="remarks"></a>Comentarios  
 A continuación, debe llamar a [RefreshLink](#refreshlink). Valor de esta propiedad está vacío para una tabla base y la lectura y escritura para una tabla asociada o un objeto no anexado a una colección.  
  
 Para obtener información relacionada, vea el tema "Propiedad SourceTableName" en la Ayuda de DAO.  
  
##  <a name="a-namesetvalidationrulea--cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule  
 Llame a esta función miembro para definir una regla de validación para una definición de tabla.  
  
```  
void SetValidationRule(LPCTSTR lpszValidationRule);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszValidationRule*  
 Puntero a una expresión de cadena que se valida una operación.  
  
### <a name="remarks"></a>Comentarios  
 Las reglas de validación se utilizan en relación con las operaciones de actualización. Si una definición de tabla contiene una regla de validación, las actualizaciones de la definición de esa tabla deben coincidir con los criterios predeterminados antes de cambian los datos. Si el cambio no coincide con los criterios, una excepción que contiene el texto de [GetValidationText](#getvalidationtext) se muestra.  
  
 Validación solo se admite para las bases de datos que utilizan el motor de base de datos Microsoft Jet. La expresión no puede hacer referencia a funciones definidas por el usuario, funciones de agregado de dominio, funciones de agregado de SQL o consultas. Una regla de validación para una `CDaoTableDef` objeto puede hacer referencia a varios campos de ese objeto.  
  
 Por ejemplo, para campos denominados `hire_date` y `termination_date`, una regla de validación puede ser:  
  
 [!code-cpp[NVC_MFCDatabase&#34;](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]  
  
 Para obtener información relacionada, vea el tema "Propiedad ValidationRule" en la Ayuda de DAO.  
  
##  <a name="a-namesetvalidationtexta--cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a>CDaoTableDef::SetValidationText  
 Llame a esta función miembro para establecer el texto de excepción de una regla de validación para una `CDaoTableDef` objeto con una tabla base subyacente admitida por el motor de base de datos Microsoft Jet.  
  
```  
void SetValidationText(LPCTSTR lpszValidationText);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszValidationText*  
 Un puntero a una expresión de cadena que especifica el texto que aparece si ha introducido datos no es válido.  
  
### <a name="remarks"></a>Comentarios  
 No se puede establecer el texto de validación de una tabla asociada.  
  
 Para obtener información relacionada, vea el tema "Propiedad texto de validación" en la Ayuda de DAO.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase (clase)](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)

