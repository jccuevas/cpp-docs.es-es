---
title: IAxWinAmbientDispatchEx (interfaz)
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: ae91921ecd5f53f4551e46e1d03cf027ce3e1f3b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292413"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx (interfaz)

Esta interfaz implementa las propiedades de ambiente complementarias para un control hospedado.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|Este método se llama para complementar la interfaz de la propiedad de ambiente predeterminada con una interfaz definida por el usuario.|

## <a name="remarks"></a>Comentarios

Esta interfaz se incluyen en las aplicaciones de ATL que se vinculan estáticamente con ATL y el host de controles ActiveX, especialmente los controles ActiveX que tiene las propiedades de ambiente. Sin incluir esta interfaz generará esta aserción: "¿Olvidó pasar el LIBID en ejecución"

Esta interfaz se expone mediante los objetos que hospeda los controles ActiveX de ATL. Deriva [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` agrega un método que permite complementar la interfaz de propiedad de ambiente proporcionada por ATL con uno propio.

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) intentará cargar la información de tipo sobre `IAxWinAmbientDispatch` y `IAxWinAmbientDispatchEx` desde la biblioteca de tipos que contiene el código.

Si vincula a ATL90.dll, **AXHost** cargará la información de tipo de la biblioteca de tipos en el archivo DLL.

Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener más detalles.

## <a name="requirements"></a>Requisitos

La definición de esta interfaz está disponible en varios formatos, como se muestra en la tabla siguiente.

|Tipo de definición|Archivo|
|---------------------|----------|
|IDL|atliface.idl|
|Biblioteca de tipos|ATL.dll|
|C++|atliface.h (que también se incluye en ATLBase.h)|

##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch

Este método se llama para complementar la interfaz de la propiedad de ambiente predeterminada con una interfaz definida por el usuario.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parámetros

*pDispatch*<br/>
Puntero a la nueva interfaz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Cuando `SetAmbientDispatch` se denomina con un puntero a una nueva interfaz, se usará esta nueva interfaz para invocar las propiedades o métodos más frecuentes para el control hospedado, si dichas propiedades no se han proporcionado por [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>Vea también

[IAxWinAmbientDispatch (interfaz)](../../atl/reference/iaxwinambientdispatch-interface.md)
