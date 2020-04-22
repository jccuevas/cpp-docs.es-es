---
title: Clase CStringData
ms.date: 11/04/2016
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
ms.openlocfilehash: f14f1d9c269f06099bd224f582de1f55da33ff0f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746839"
---
# <a name="cstringdata-class"></a>Clase CStringData

Esta clase representa los datos de un objeto de cadena.

## <a name="syntax"></a>Sintaxis

```
struct CStringData
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddRef](#addref)|Incrementa el recuento de referencias del objeto de datos de cadena.|
|[datos](#data)|Recupera los datos de caracteres de un objeto de cadena.|
|[IsLocked](#islocked)|Determina si el búfer del objeto de cadena asociado está bloqueado.|
|[IsShared](#isshared)|Determina si el búfer del objeto de cadena asociado se comparte actualmente.|
|[Bloquear](#lock)|Bloquea el búfer del objeto de cadena asociado.|
|[Versión](#release)|Libera el objeto de cadena especificado.|
|[Desbloquear](#unlock)|Desbloquea el búfer del objeto de cadena asociado.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[nAllocLength](#nalloclength)|Longitud de los `XCHAR`datos asignados en s (sin incluir la terminación de null)|
|[nDataLength](#ndatalength)|Longitud de los `XCHAR`datos utilizados actualmente en s (sin incluir la terminación de null)|
|[nRefs](#nrefs)|El recuento de referencias actual del objeto.|
|[pStringMgr](#pstringmgr)|Un puntero al administrador de cadenas de este objeto de cadena.|

## <a name="remarks"></a>Observaciones

Esta clase solo la deben usar los desarrolladores que implementan administradores de cadenas personalizados. Para obtener más información sobre los administradores de cadenas personalizados, consulte [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

Esta clase encapsula varios tipos de información y datos asociados a un objeto de cadena superior, como [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)o [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) objetos. Cada objeto de cadena superior `CStringData` contiene un puntero a su objeto asociado, lo que permite que varios objetos de cadena apunten al mismo objeto de datos de cadena. Esta relación se representa mediante`nRefs`el recuento `CStringData` de referencias ( ) del objeto.

> [!NOTE]
> En algunos casos, un tipo `CFixedString`de cadena (como ) no compartirá un objeto de datos de cadena con más de un objeto de cadena superior. Para obtener más información al respecto, vea [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

Estos datos se componen de:

- El administrador de memoria (de tipo [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) de la cadena.

- La longitud actual ( [nDataLength](#ndatalength)) de la cadena.

- La longitud asignada ( [nAllocLength](#nalloclength)) de la cadena. Por razones de rendimiento, esto puede diferir de la longitud de cadena actual

- El recuento de referencias actual ( `CStringData` [nRefs](#nrefs)) del objeto. Este valor se utiliza para determinar cuántos `CStringData` objetos de cadena comparten el mismo objeto.

- El búfer de caracteres real ( [datos](#data)) de la cadena.

   > [!NOTE]
   > El administrador de cadenas asigna el búfer de caracteres real `CStringData` del objeto de cadena y se anexa al objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpstr.h

## <a name="cstringdataaddref"></a><a name="addref"></a>CStringData::AddRef

Incrementa el recuento de referencias del objeto de cadena.

```cpp
void AddRef() throw();
```

### <a name="remarks"></a>Observaciones

Incrementa el recuento de referencias del objeto de cadena.

> [!NOTE]
> No llame a este método en una cadena con un recuento de referencias negativo, ya que un recuento negativo indica que el búfer de cadena está bloqueado.

## <a name="cstringdatadata"></a><a name="data"></a>CStringData::data

Devuelve un puntero al búfer de caracteres de un objeto de cadena.

```cpp
void* data() throw();
```

### <a name="return-value"></a>Valor devuelto

Puntero al búfer de caracteres del objeto de cadena.

### <a name="remarks"></a>Observaciones

Llame a esta función para devolver el búfer de caracteres actual del objeto de cadena asociado.

> [!NOTE]
> Este búfer no es `CStringData` asignado por el objeto, sino por el administrador de cadenas cuando sea necesario. Cuando se asigna, el búfer se anexa al objeto de datos de cadena.

## <a name="cstringdataislocked"></a><a name="islocked"></a>CStringData::IsLocked

Determina si el búfer de caracteres está bloqueado.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el búfer está bloqueado; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Llame a esta función para determinar si el búfer de caracteres de un objeto de cadena está bloqueado actualmente.

## <a name="cstringdataisshared"></a><a name="isshared"></a>CStringData::IsShared

Determina si se comparte el búfer de caracteres.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se comparte el búfer; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Llame a esta función para determinar si el búfer de caracteres de un objeto de datos de cadena se comparte actualmente entre varios objetos de cadena.

## <a name="cstringdatalock"></a><a name="lock"></a>CStringData::Lock

Bloquea el búfer de caracteres del objeto de cadena asociado.

```cpp
void Lock() throw();
```

### <a name="remarks"></a>Observaciones

Llame a esta función para bloquear el búfer de caracteres del objeto de datos de cadena. El bloqueo y desbloqueo se utiliza cuando el desarrollador requiere acceso directo al búfer de caracteres. Un buen ejemplo de bloqueo se muestra mediante el `CSimpleStringT` [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) y [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) métodos de .

> [!NOTE]
> Un búfer de caracteres solo se puede bloquear si el búfer no se comparte entre objetos de cadena superior.

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a>CStringData::nAllocLength

Longitud del búfer de caracteres asignado.

```
int nAllocLength;
```

### <a name="remarks"></a>Observaciones

Almacena la longitud del búfer `XCHAR`de datos asignado en s (sin incluir la terminación de null).

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a>CStringData::nDataLength

Longitud actual del objeto de cadena.

```
int nDataLength;
```

### <a name="remarks"></a>Observaciones

Almacena la longitud de `XCHAR`los datos utilizados actualmente en s (sin incluir la terminación de null).

## <a name="cstringdatanrefs"></a><a name="nrefs"></a>CStringData::nRefs

Recuento de referencias del objeto de datos de cadena.

```
long nRefs;
```

### <a name="remarks"></a>Observaciones

Almacena el recuento de referencias del objeto de datos de cadena. Este recuento indica el número de objetos de cadena superiores que están asociados con el objeto de datos de cadena. Un valor negativo indica que el objeto de datos de cadena está bloqueado actualmente.

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a>CStringData::pStringMgr

El administrador de memoria del objeto de cadena asociado.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Observaciones

Almacena el administrador de memoria para el objeto de cadena asociado. Para obtener más información sobre los administradores de memoria y las cadenas, vea [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringdatarelease"></a><a name="release"></a>CStringData::Release

Disminuye el recuento de referencias del objeto de datos de cadena.

```cpp
void Release() throw();
```

### <a name="remarks"></a>Observaciones

Llame a esta función para disminuir el `CStringData` recuento de referencias, liberando la estructura si el recuento de referencias llega a cero. Esto se suele hacer cuando se elimina un objeto de cadena y, por lo tanto, ya no es necesario hacer referencia al objeto de datos de cadena.

Por ejemplo, el código `CStringData::Release` siguiente llamaría al `str1`objeto de datos de cadena asociado a:

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a>CStringData::Unlock

Desbloquea el búfer de caracteres del objeto de cadena asociado.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>Observaciones

Llame a esta función para desbloquear el búfer de caracteres del objeto de datos de cadena. Una vez que se desbloquea un búfer, se puede compartir y se puede contar la referencia.

> [!NOTE]
> Cada llamada `Lock` a debe coincidir con `Unlock`una llamada correspondiente a .

El bloqueo y el desbloqueo se usan cuando el desarrollador debe asegurarse de que los datos de cadena no se comparten. Un buen ejemplo de bloqueo se muestra mediante el `CSimpleStringT` [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) y [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) métodos de .

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
