---
title: Marshaling Global Functions
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: b839e93b6251a09ce79df60a49b4054d1af76cc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326259"
---
# <a name="marshaling-global-functions"></a>Marshaling Global Functions

Estas funciones proporcionan compatibilidad para calcular el cálculo de referencias y convertir datos de cálculo de referencias en punteros de interfaz.

> [!IMPORTANT]
> Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Libera los datos `IStream` de cálculo de referencias y el puntero.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Crea un nuevo objeto de secuencia y calcula las referencias del puntero de interfaz especificado.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|Convierte los datos de cálculo de referencias de una secuencia en un puntero de interfaz.|

## <a name="requirements"></a>Requisitos:

**Encabezado:** atlbase.h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a>AtlFreeMarshalStream

Libera los datos de serializar del flujo; a continuación, libera el puntero del flujo.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
[en] Un puntero `IStream` a la interfaz en la secuencia utilizada para el cálculo de referencias.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc

Crea un nuevo objeto de flujo, escribe el CLSID del proxy en el flujo y calcula las referencias del puntero de interfaz especificado escribiendo los datos necesarios para inicializar el proxy en el flujo.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
[en] Un puntero a la interfaz que se va a serializar.

*Iid*<br/>
[en] Guid de la interfaz que se va a calcular.

*ppStream*<br/>
[fuera] Puntero a `IStream` la interfaz en el nuevo objeto de secuencia utilizado para el cálculo de referencias.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El indicador MSHLFLAGS_TABLESTRONG se establece para que el puntero se pueda serializar en varias secuencias. El puntero también se puede desclasificar varias veces.

Si se produce un error en el cálculo de referencias, se libera el puntero de secuencia.

`AtlMarshalPtrInProc`solo se puede utilizar en un puntero a un objeto en proceso.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a>AtlUnmarshalPtr

Convierte los datos de cálculo de referencias del flujo en un puntero de interfaz que puede usarse en el cliente.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
[en] Puntero a la secuencia que se va a desclasificar.

*Iid*<br/>
[en] Guid de la interfaz que se va a desclasificar.

*ppUnk*<br/>
[fuera] Un puntero a la interfaz sin serializar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)
