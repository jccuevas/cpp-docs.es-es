---
title: Interfaz IAxWinAmbientDispatchEx | Documentos de Microsoft
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
ms.openlocfilehash: 22815ddf3131b9d262d68a3202f4f500b7edf807
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358145"
---
# <a name="iaxwinambientdispatchex-interface"></a>Interfaz IAxWinAmbientDispatchEx
Esta interfaz implementa las propiedades de ambiente complementarios para un control hospedado.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[SetAmbientDispatch](#setambientdispatch)|Se llama a este método para complementar la interfaz de la propiedad de ambiente predeterminada con una interfaz definida por el usuario.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se incluyen en las aplicaciones de ATL se vinculan estáticamente con ATL y el host controles ActiveX, especialmente los controles de ActiveX que tienen propiedades de ambiente. Sin incluir esta interfaz generará esta aserción: "¿Compruebe si olvidó pasar LIBID en ejecución"  
  
 Esta interfaz se expone mediante objetos que hospeda los controles ActiveX de ATL. Deriva [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` agrega un método que permite complementar la interfaz de la propiedad de ambiente proporcionada por ATL con uno de sus propios.  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) intentará cargar la información de tipo sobre `IAxWinAmbientDispatch` y `IAxWinAmbientDispatchEx` desde la biblioteca de tipos que contiene el código.  
  
 Si está vinculando ATL90.dll, **AXHost** cargará la información de tipo de la biblioteca de tipos del archivo DLL.  
  
 Vea [hospedaje de controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener más detalles.  
  
## <a name="requirements"></a>Requisitos  
 La definición de esta interfaz está disponible en varios formatos, como se muestra en la tabla siguiente.  
  
|Tipo de definición|Archivo|  
|---------------------|----------|  
|IDL|atliface.idl|  
|Biblioteca de tipos|ATL.dll|  
|C++|atliface.h (que también se incluye en ATLBase.h)|  
  
##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch  
 Se llama a este método para complementar la interfaz de la propiedad de ambiente predeterminada con una interfaz definida por el usuario.  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 *pDispatch*  
 Puntero a la nueva interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `SetAmbientDispatch` se llama con un puntero a una nueva interfaz, se utilizará esta nueva interfaz para invocar las propiedades o métodos solicitadas por el control hospedado, si las propiedades no se han proporcionado por [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
## <a name="see-also"></a>Vea también  
 [IAxWinAmbientDispatch (interfaz)](../../atl/reference/iaxwinambientdispatch-interface.md)
