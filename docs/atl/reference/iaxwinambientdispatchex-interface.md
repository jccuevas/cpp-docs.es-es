---
title: Interfaz IAxWinAmbientDispatchEx | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatchEx
- No header/ATL::IAxWinAmbientDispatchEx
- No header/ATL::SetAmbientDispatch
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
caps.latest.revision: 25
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 915514a021aa89b751a49a34cb53b693b9fd0c45
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="iaxwinambientdispatchex-interface"></a>Interfaz IAxWinAmbientDispatchEx
Esta interfaz implementa las propiedades de ambientales adicionales para un control hospedado.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
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
 Esta interfaz se incluyen en las aplicaciones de ATL que se vinculan estáticamente con ATL y el host de controles ActiveX, especialmente los controles ActiveX que tienen propiedades de ambiente. Sin incluir esta interfaz generará esta aserción: "¿ha olvidado pasar el identificador LIBID a ejecución"  
  
 Esta interfaz expone objetos que hospeda los controles ActiveX de ATL. Deriva [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` agrega un método que permite complementar la interfaz de la propiedad de ambiente de ATL con uno de sus propios.  
  
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
  
##  <a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch  
 Este método se llama para complementar la interfaz de la propiedad de ambiente predeterminada con una interfaz definida por el usuario.  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 *pDispatch*  
 Puntero a la nueva interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `SetAmbientDispatch` se llama con un puntero a una nueva interfaz, se utilizará esta nueva interfaz para invocar las propiedades o métodos solicitadas por el control hospedado, si dichas propiedades no se han proporcionado por [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)

