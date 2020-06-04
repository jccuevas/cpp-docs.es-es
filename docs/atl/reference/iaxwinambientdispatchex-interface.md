---
title: Interfaz IAxWinAmbientDispatchEx
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: f4816846801e388619db62998ec979a1100916ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329978"
---
# <a name="iaxwinambientdispatchex-interface"></a>Interfaz IAxWinAmbientDispatchEx

Esta interfaz implementa propiedades ambientales suplementarias para un control hospedado.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|Se llama a este método para complementar la interfaz de propiedad ambiental predeterminada con una interfaz definida por el usuario.|

## <a name="remarks"></a>Observaciones

Incluya esta interfaz en aplicaciones ATL que están vinculadas estáticamente a ATL y hospedan controles ActiveX, especialmente controles ActiveX que tienen propiedades ambientales. Sin incluir esta interfaz generará esta aserción: "¿Olvidó pasar el LIBID a CComModule::Init"

Esta interfaz se expone mediante objetos de hospedaje de control ActiveX de ATL. Derivado de [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` agrega un método que le permite complementar la interfaz de propiedad ambiental proporcionada por ATL con una propia.

<xref:System.Windows.Forms.AxHost>intentará cargar información de `IAxWinAmbientDispatch` `IAxWinAmbientDispatchEx` tipo sobre y desde la biblioteca de tipos que contiene el código.

Si está vinculando a ATL90.dll, **AXHost** cargará la información de tipo de la biblioteca de tipos en el archivo DLL.

Consulte [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener más detalles.

## <a name="requirements"></a>Requisitos

La definición de esta interfaz está disponible en varios formularios, como se muestra en la tabla siguiente.

|Tipo de definición|Archivo|
|---------------------|----------|
|Idl|atliface.idl|
|Biblioteca de tipos|Atl.dll|
|C++|atliface.h (también incluido en ATLBase.h)|

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Se llama a este método para complementar la interfaz de propiedad ambiental predeterminada con una interfaz definida por el usuario.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parámetros

*pDispatch*<br/>
Puntero a la nueva interfaz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Cuando `SetAmbientDispatch` se llama con un puntero a una nueva interfaz, esta nueva interfaz se usará para invocar las propiedades o métodos solicitados por el control hospedado, si [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)no proporciona ya esas propiedades.

## <a name="see-also"></a>Consulte también

[Interfaz IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)
