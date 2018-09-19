---
title: IAxWinAmbientDispatchEx (interfaz) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e579c537421eba0f3b9dbcf347e08b6691cddb21
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022219"
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

Esta interfaz se incluyen en las aplicaciones de ATL que se vinculan estáticamente con ATL y el host de controles ActiveX, especialmente los controles ActiveX que tiene las propiedades de ambiente. Sin incluir esta interfaz generará esta aserción: "¿olvidó pasar el LIBID en ejecución"

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
