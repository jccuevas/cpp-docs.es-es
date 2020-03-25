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
ms.openlocfilehash: 97a79dee826dfba4b42053bbeba8c65e4d2b429c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211190"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl (Clase)

Proporciona una implementación de conjunto de filas de OLE DB estándar sin requerir la herencia múltiple de muchas interfaces de implementación.

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
Clase del usuario que se deriva de `CRowsetImpl`.

*Storage*<br/>
La clase de registro de usuario.

*CreatorClass*<br/>
La clase que contiene las propiedades del conjunto de filas; Normalmente, el comando.

*ArrayType*<br/>
La clase que actuará como almacenamiento para los datos del conjunto de filas. El valor predeterminado de este parámetro es `CAtlArray`, pero puede ser cualquier clase que admita la funcionalidad necesaria.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[NameFromDBID](#namefromdbid)|Extrae una cadena de un `DBID` y la copia en el *BSTR* pasado.|
|[SetCommandText](#setcommandtext)|Valida y almacena los `DBID`s en las dos cadenas ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|

### <a name="overridable-methods"></a>Métodos reemplazables

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|Recupera información de columna para una solicitud de cliente determinada.|
|[GetCommandFromID](#getcommandfromid)|Comprueba si uno o ambos parámetros contienen valores de cadena y, en ese caso, copia los valores de cadena en los miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|
|[ValidateCommandID](#validatecommandid)|Comprueba si una o ambas `DBID`contienen valores de cadena y, en ese caso, los copia en sus miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_rgRowData](#rgrowdata)|De forma predeterminada, un `CAtlArray` que templatizes en el argumento de la plantilla de registro de usuario para `CRowsetImpl`. Otra clase de tipo de matriz se puede usar si se cambia el argumento de plantilla `ArrayType` a `CRowsetImpl`.|
|[m_strCommandText](#strcommandtext)|Contiene el comando inicial del conjunto de filas.|
|[m_strIndexText](#strindextext)|Contiene el índice inicial del conjunto de filas.|

## <a name="remarks"></a>Observaciones

`CRowsetImpl` proporciona invalidaciones en forma de conversiones estáticas. Los métodos controlan la manera en que un conjunto de filas determinado validará el texto del comando. Puede crear su propia clase de estilo `CRowsetImpl`si hace que las interfaces de implementación sean múltiples heredadas. El único método para el que se debe proporcionar la implementación es `Execute`. En función del tipo de conjunto de filas que esté creando, los métodos del creador esperarán firmas diferentes para `Execute`. Por ejemplo, si usa una clase derivada de `CRowsetImpl`para implementar un conjunto de filas de esquema, el método `Execute` tendrá la firma siguiente:

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

Si va a crear una clase derivada de `CRowsetImpl`para implementar un conjunto de filas de comando o de sesión, el método `Execute` tendrá la siguiente firma:

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

Para implementar cualquiera de los métodos `Execute` derivados de `CRowsetImpl`, debe rellenar los búferes de datos internos ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).

## <a name="crowsetimplnamefromdbid"></a><a name="namefromdbid"></a>CRowsetImpl:: NameFromDBID

Extrae una cadena de un `DBID` y la copia en el *BSTR* pasado.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>Parámetros

*pDBID*<br/>
de Puntero a la `DBID` desde la que se va a extraer una cadena.

*utilicen*<br/>
de Referencia [CComBSTR](../../atl/reference/ccombstr-class.md) para colocar una copia de la cadena de `DBID`.

*bIndex*<br/>
de **true** si `DBID`un índice; **false** si `DBID`una tabla.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar. Dependiendo de si el `DBID` es una tabla o un índice (indicado por *bIndex*), el método devolverá DB_E_NOINDEX o DB_E_NOTABLE.

### <a name="remarks"></a>Observaciones

Este método lo llaman las implementaciones de `CRowsetImpl` de [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) y [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md).

## <a name="crowsetimplsetcommandtext"></a><a name="setcommandtext"></a>CRowsetImpl:: SetCommandText

Valida y almacena los `DBID`s en las dos cadenas ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parámetros

*pTableID*<br/>
de Puntero a la `DBID` que representa el identificador de la tabla.

*pIndexID*<br/>
de Puntero a la `DBID` que representa el identificador del índice.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

`CreateRowset`llama al método `SetCommentText`, un método hace plantilla estático de `IOpenRowsetImpl`.

Este método delega su trabajo mediante una llamada a [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) y [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) a través de un puntero de conversión.

## <a name="crowsetimplgetcolumninfo"></a><a name="getcolumninfo"></a>CRowsetImpl:: GetColumnInfo

Recupera información de columna para una solicitud de cliente determinada.

### <a name="syntax"></a>Sintaxis

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>Parámetros

*FV*<br/>
de Puntero a la clase derivada del `CRowsetImpl` del usuario.

*pcCols*<br/>
de Puntero (salida) al número de columnas devueltas.

### <a name="return-value"></a>Valor devuelto

Puntero a una estructura de `ATLCOLUMNINFO` estática.

### <a name="remarks"></a>Observaciones

Este método es una invalidación avanzada.

Varias clases de implementación base llaman a este método para recuperar información de columna para una solicitud de cliente determinada. Normalmente, este método sería llamado por `IColumnsInfoImpl`. Si invalida este método, debe colocar una versión del método en la clase derivada de `CRowsetImpl`. Dado que el método se puede colocar en una clase que no es hace plantilla, debe cambiar *PV* a la clase derivada de `CRowsetImpl`adecuada.

En el siguiente ejemplo se muestra el uso de `GetColumnInfo`. En este ejemplo, `CMyRowset` es una clase derivada de `CRowsetImpl`. Para invalidar `GetColumnInfo` para todas las instancias de esta clase, coloque el método siguiente en la definición de clase de `CMyRowset`:

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="crowsetimplgetcommandfromid"></a><a name="getcommandfromid"></a>CRowsetImpl:: GetCommandFromID

Comprueba si uno o ambos parámetros contienen valores de cadena y, en ese caso, copia los valores de cadena en los miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parámetros

*pTableID*<br/>
de Puntero a la `DBID` que representa el identificador de la tabla.

*pIndexID*<br/>
de Puntero a la `DBID` que representa el identificador del índice.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Se llama a este método a través de una conversión de tipos estática por `CRowsetImpl` para rellenar los miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). De forma predeterminada, este método comprueba si uno o ambos parámetros contienen valores de cadena. Si contienen valores de cadena, este método copia los valores de cadena en los miembros de datos. Al colocar un método con esta firma en la clase derivada de `CRowsetImpl`, se llamará al método en lugar de a la implementación base.

## <a name="crowsetimplvalidatecommandid"></a><a name="validatecommandid"></a>CRowsetImpl:: ValidateCommandID

Comprueba si una o ambas `DBID`contienen valores de cadena y, en ese caso, los copia en sus miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parámetros

*pTableID*<br/>
de Puntero a la `DBID` que representa el identificador de la tabla.

*pIndexID*<br/>
de Puntero a la `DBID` que representa el identificador del índice.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Se llama a este método a través de una conversión de tipos estática por `CRowsetImpl` para rellenar sus miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). De forma predeterminada, este método comprueba si una o ambas `DBID`contienen valores de cadena y, en ese caso, los copia en sus miembros de datos. Al colocar un método con esta firma en la clase derivada de `CRowsetImpl`, se llamará al método en lugar de a la implementación base.

## <a name="crowsetimplm_rgrowdata"></a><a name="rgrowdata"></a>CRowsetImpl:: m_rgRowData

De forma predeterminada, un `CAtlArray` que templatizes en el argumento de la plantilla de registro de usuario para `CRowsetImpl`.

### <a name="syntax"></a>Sintaxis

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>Observaciones

*ArrayType* es un parámetro de plantilla para `CRowsetImpl`.

## <a name="crowsetimplm_strcommandtext"></a><a name="strcommandtext"></a>CRowsetImpl:: m_strCommandText

Contiene el comando inicial del conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="crowsetimplm_strindextext"></a><a name="strindextext"></a>CRowsetImpl:: m_strIndexText

Contiene el índice inicial del conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```
