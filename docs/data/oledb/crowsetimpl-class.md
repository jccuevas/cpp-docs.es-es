---
title: CRowsetImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- GetColumnInfo
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
- CRowsetImpl::m_strCommandText
- CRowsetImpl.m_strCommandText
- CRowsetImpl::m_strIndexText
- CRowsetImpl.m_strIndexText
helpviewer_keywords:
- CRowsetImpl class
- NameFromDBID method
- SetCommandText method
- GetColumnInfo method
- GetCommandFromID method
- ValidateCommandID method
- m_rgRowData
- m_strCommandText
- m_strIndexText
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
ms.openlocfilehash: 1fac3a74ca259fe3b680355fadc7f9bbd6e3cc13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368713"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl (Clase)

Proporciona una implementación de conjunto de filas de OLE DB estándar sin necesidad de herencia múltiple de cuántas interfaces de implementación.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   class T,
   class Storage,
   class CreatorClass,
   class ArrayType = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class RowsetInterface = IRowsetImpl <T, IRowset>
>
class CRowsetImpl : 
   public CComObjectRootEx<CreatorClass::_ThreadModel>,
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase del usuario que se deriva de `CRowsetImpl`.

*Storage*<br/>
La clase de registro de usuario.

*CreatorClass*<br/>
La clase que contiene las propiedades para el conjunto de filas; Normalmente, el comando.

*ArrayType*<br/>
La clase que actuará como almacenamiento de datos del conjunto de filas. Valor predeterminado de este parámetro es `CAtlArray`, pero puede ser cualquier clase que admita la funcionalidad necesaria.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[NameFromDBID](#namefromdbid)|Extrae una cadena de un `DBID` y lo copia en el *bstr* pasado.|
|[SetCommandText](#setcommandtext)|Valida y almacena el `DBID`s en las dos cadenas ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|

### <a name="overridable-methods"></a>Métodos reemplazables

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Recupera información de columna para una solicitud de cliente en particular.|
|[GetCommandFromID](#getcommandfromid)|Comprueba si uno o ambos parámetros contienen los valores de cadena y si es así, copia los valores de cadena a los miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|
|[ValidateCommandID](#validatecommandid)|Comprueba para ver si alguno o ambos `DBID`s contienen valores de cadena y si es así, los copia en sus miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_rgRowData](#rgrowdata)|De forma predeterminada, un `CAtlArray` que templatizes en el argumento de plantilla de registro de usuario para `CRowsetImpl`. Se puede utilizar otra clase de tipo de matriz cambiando el `ArrayType` argumento de plantilla para `CRowsetImpl`.|
|[m_strCommandText](#strcommandtext)|Contiene comandos inicial del conjunto de filas.|
|[m_strIndexText](#strindextext)|Contiene el índice inicial del conjunto de filas.|

## <a name="remarks"></a>Comentarios

`CRowsetImpl` Proporciona reemplazos en forma de convierte estático. Los métodos de controlan la forma en que un conjunto de filas determinado validará el texto del comando. Puede crear sus propios `CRowsetImpl`-clase de estilo mediante la realización de las interfaces de la implementación heredada de varios. El único método para el que debe proporcionar la implementación es `Execute`. Dependiendo de qué tipo de conjunto de filas está creando, los métodos de creador esperará firmas diferentes para `Execute`. Por ejemplo, si está utilizando un `CRowsetImpl`-clase derivada para implementar un conjunto de filas de esquema, el `Execute` método tendrá la siguiente firma:

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

Si está creando un `CRowsetImpl`-clase derivada para implementar un comando o un conjunto de filas de la sesión, el `Execute` método tendrá la siguiente firma:

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

Para implementar cualquiera de los `CRowsetImpl`-derivado `Execute` métodos, debe rellenar los búferes de datos interno ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).

## <a name="namefromdbid"></a> CRowsetImpl::NameFromDBID

Extrae una cadena de un `DBID` y lo copia en el *bstr* pasado.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>Parámetros

*pDBID*<br/>
[in] Un puntero a la `DBID` desde la que se va a extraer una cadena.

*bstr*<br/>
[in] Un [CComBSTR](../../atl/reference/ccombstr-class.md) referencia para colocar una copia de la `DBID` cadena.

*bIndex*<br/>
[in] **true** si un índice `DBID`; **false** si una tabla `DBID`.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar. Dependiendo de si el `DBID` es una tabla o un índice (indicado por *bIndex*), el método devolverá DB_E_NOINDEX o DB_E_NOTABLE.

### <a name="remarks"></a>Comentarios

Este método es invocado por el `CRowsetImpl` implementací [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) y [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md).

## <a name="setcommandtext"></a> CRowsetImpl::SetCommandText

Valida y almacena el `DBID`s en las dos cadenas ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parámetros

*pTableID*<br/>
[in] Un puntero a la `DBID` que representa el identificador de tabla.

*pIndexID*<br/>
[in] Un puntero a la `DBID` que representa el identificador de índice.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

El `SetCommentText` llama al método `CreateRowset`, estático hace plantilla método `IOpenRowsetImpl`.

Este método delega su trabajo mediante una llamada a [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) y [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) mediante un puntero de conversión hacia arriba.

## <a name="getcolumninfo"></a> CRowsetImpl::GetColumnInfo

Recupera información de columna para una solicitud de cliente en particular.

### <a name="syntax"></a>Sintaxis

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>Parámetros

*pv*<br/>
[in] Un puntero para el usuario `CRowsetImpl` clase derivada.

*pcCols*<br/>
[in] Un puntero (salida) para el número de columnas devueltas.

### <a name="return-value"></a>Valor devuelto

Un puntero a una variable static `ATLCOLUMNINFO` estructura.

### <a name="remarks"></a>Comentarios

Este método es un reemplazo avanzado.

Este método llama a varias clases de implementación base para recuperar la información de columna para una solicitud de cliente en particular. Normalmente, este método podría llamarse `IColumnsInfoImpl`. Si invalida este método, debe colocar una versión del método en su `CRowsetImpl`-clase derivada. Dado que el método se puede colocar en una clase que no son de plantilla, debe cambiar *pv* correspondientes `CRowsetImpl`-clase derivada.

En el ejemplo siguiente se muestra `GetColumnInfo` uso. En este ejemplo, `CMyRowset` es un `CRowsetImpl`-clase derivada. Con el fin de invalidar `GetColumnInfo` para todas las instancias de esta clase, coloque el siguiente método en el `CMyRowset` definición de clase:

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="getcommandfromid"></a> CRowsetImpl::GetCommandFromID

Comprueba si uno o ambos parámetros contienen los valores de cadena y si es así, copia los valores de cadena a los miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parámetros

*pTableID*<br/>
[in] Un puntero a la `DBID` que representa el identificador de tabla.

*pIndexID*<br/>
[in] Un puntero a la `DBID` que representa el identificador de índice.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Este método se llama a través de una conversión hacia arriba estático por `CRowsetImpl` para rellenar los miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). De forma predeterminada, este método comprueba si uno o ambos parámetros contienen los valores de cadena. Si contienen los valores de cadena, este método copia los valores de cadena a los miembros de datos. Mediante la colocación de un método con esta firma en su `CRowsetImpl`-clase derivada, el método se llamará en lugar de la implementación base.

## <a name="validatecommandid"></a> CRowsetImpl::ValidateCommandID

Comprueba para ver si alguno o ambos `DBID`s contienen valores de cadena y si es así, los copia en sus miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parámetros

*pTableID*<br/>
[in] Un puntero a la `DBID` que representa el identificador de tabla.

*pIndexID*<br/>
[in] Un puntero a la `DBID` que representa el identificador de índice.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Este método se llama a través de una conversión hacia arriba estático por `CRowsetImpl` para rellenar sus miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). De forma predeterminada, este método comprueba para ver si alguno o ambos `DBID`s contienen valores de cadena y si es así, los copia en sus miembros de datos. Mediante la colocación de un método con esta firma en su `CRowsetImpl`-clase derivada, el método se llamará en lugar de la implementación base.

## <a name="rgrowdata"></a> CRowsetImpl::m_rgRowData

De forma predeterminada, un `CAtlArray` que templatizes en el argumento de plantilla de registro de usuario para `CRowsetImpl`.

### <a name="syntax"></a>Sintaxis

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>Comentarios

*ArrayType* es un parámetro de plantilla `CRowsetImpl`.

## <a name="strcommandtext"></a> CRowsetImpl::m_strCommandText

Contiene comandos inicial del conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="strindextext"></a> CRowsetImpl::m_strIndexText

Contiene el índice inicial del conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```