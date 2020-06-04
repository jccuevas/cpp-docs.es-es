---
title: CUtlProps (Clase)
ms.date: 11/04/2016
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
ms.openlocfilehash: 3498ec1250d9443007acb3b12ec25983a71587d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211112"
---
# <a name="cutlprops-class"></a>CUtlProps (Clase)

Implementa propiedades para una variedad de interfaces de propiedad OLE DB (por ejemplo, `IDBProperties`, `IDBProperties`y `IRowsetInfo`).

## <a name="syntax"></a>Sintaxis

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase que contiene el `BEGIN_PROPSET_MAP`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[GetPropValue](#getpropvalue)|Obtiene una propiedad de un conjunto de propiedades.|
|[IsValidValue](#isvalidvalue)|Se utiliza para validar un valor antes de establecer una propiedad.|
|[OnInterfaceRequested](#oninterfacerequested)|Administra las solicitudes de una interfaz opcional cuando un consumidor llama a un método en una interfaz de creación de objetos.|
|[OnPropertyChanged](#onpropertychanged)|Se llama después de establecer una propiedad para controlar las propiedades encadenadas.|
|[SetPropValue](#setpropvalue)|Establece una propiedad en un conjunto de propiedades.|

## <a name="remarks"></a>Observaciones

La mayor parte de esta clase es un detalle de implementación.

`CUtlProps` contiene dos miembros para establecer las propiedades internamente: [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) y [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).

Para obtener más información sobre las macros utilizadas en una asignación de conjunto de propiedades, vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) y [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).

## <a name="cutlpropsgetpropvalue"></a><a name="getpropvalue"></a>CUtlProps:: GetPropValue

Obtiene una propiedad de un conjunto de propiedades.

### <a name="syntax"></a>Sintaxis

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parámetros

*pguidPropSet*<br/>
de GUID de PropSet.

*dwPropId*<br/>
de Índice de la propiedad.

*pvValue*<br/>
enuncia Puntero a una variante que contiene el nuevo valor de propiedad.

### <a name="return-value"></a>Valor devuelto

`Failure` en caso de error y S_OK si se realiza correctamente.

## <a name="cutlpropsisvalidvalue"></a><a name="isvalidvalue"></a>CUtlProps:: IsValidValue

Se utiliza para validar un valor antes de establecer una propiedad.

### <a name="syntax"></a>Sintaxis

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parámetros

*iCurSet*<br/>
Índice de la matriz del conjunto de propiedades; cero si solo hay un conjunto de propiedades.

*pDBProp*<br/>
El identificador de propiedad y el nuevo valor en una estructura [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85)) .

### <a name="return-value"></a>Valor devuelto

HRESULT estándar. El valor devuelto predeterminado es S_OK.

### <a name="remarks"></a>Observaciones

Si tiene alguna rutina de validación que desee ejecutar en un valor que va a usar para establecer una propiedad, debe invalidar esta función. Por ejemplo, podría validar DBPROP_AUTH_PASSWORD en una tabla de contraseñas para determinar un valor válido.

## <a name="cutlpropsoninterfacerequested"></a><a name="oninterfacerequested"></a>CUtlProps:: OnInterfaceRequested

Administra las solicitudes de una interfaz opcional cuando un consumidor llama a un método en una de las interfaces de creación de objetos.

### <a name="syntax"></a>Sintaxis

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>Parámetros

*riid*<br/>
de IID de la interfaz solicitada. Para obtener más información, vea la descripción del parámetro *riid* de `ICommand::Execute` en la *Referencia del programador de OLE DB* (en *MDAC SDK*).

### <a name="remarks"></a>Observaciones

`OnInterfaceRequested` controla las solicitudes de consumidor de una interfaz opcional cuando un consumidor llama a un método en una de las interfaces de creación de objetos (como `IDBCreateSession`, `IDBCreateCommand`, `IOpenRowset`o `ICommand`). Establece la propiedad OLE DB correspondiente para la interfaz solicitada. Por ejemplo, si el consumidor solicita `IID_IRowsetLocate`, `OnInterfaceRequested` establece la interfaz `DBPROP_IRowsetLocate`. Al hacerlo, se mantiene el estado correcto durante la creación del conjunto de filas.

Se llama a este método cuando el consumidor llama a `IOpenRowset::OpenRowset` o `ICommand::Execute`.

Si un consumidor abre un objeto y solicita una interfaz opcional, el proveedor debe establecer la propiedad asociada a esa interfaz en VARIANT_TRUE. Para permitir el procesamiento específico de la propiedad, se llama a `OnInterfaceRequested` antes de que se llame al método de `Execute` del proveedor. De forma predeterminada, `OnInterfaceRequested` controla las siguientes interfaces:

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

Si desea controlar otras interfaces, invalide esta función en el origen de datos, la sesión, el comando o la clase de conjunto de filas para procesar funciones. La invalidación debe pasar por las interfaces normales set/get properties para asegurarse de que las propiedades de configuración también establecen las propiedades encadenadas (vea [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)).

## <a name="cutlpropsonpropertychanged"></a><a name="onpropertychanged"></a>CUtlProps:: OnPropertyChanged

Se llama después de establecer una propiedad para controlar las propiedades encadenadas.

### <a name="syntax"></a>Sintaxis

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parámetros

*iCurSet*<br/>
Índice de la matriz del conjunto de propiedades; cero si solo hay un conjunto de propiedades.

*pDBProp*<br/>
El identificador de propiedad y el nuevo valor en una estructura [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85)) .

### <a name="return-value"></a>Valor devuelto

HRESULT estándar. El valor devuelto predeterminado es S_OK.

### <a name="remarks"></a>Observaciones

Si desea controlar las propiedades encadenadas, como marcadores o actualizaciones cuyos valores dependen del valor de otra propiedad, debe invalidar esta función.

### <a name="example"></a>Ejemplo

En esta función, el usuario obtiene el identificador de propiedad del parámetro `DBPROP*`. Ahora, es posible comparar el identificador con una propiedad para la cadena. Cuando se encuentra la propiedad, se llama a `SetProperties` con la propiedad que ahora se establecerá junto con la otra propiedad. En este caso, si uno obtiene la propiedad `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`o `DBPROP_ORDEREDBOOKMARKS`, puede establecer la propiedad `DBPROP_BOOKMARKS`.

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="cutlpropssetpropvalue"></a><a name="setpropvalue"></a>CUtlProps:: SetPropValue

Establece una propiedad en un conjunto de propiedades.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parámetros

*pguidPropSet*<br/>
de GUID de PropSet.

*dwPropId*<br/>
de Índice de la propiedad.

*pvValue*<br/>
de Puntero a una variante que contiene el nuevo valor de propiedad.

### <a name="return-value"></a>Valor devuelto

`Failure` en caso de error y S_OK si se realiza correctamente.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
