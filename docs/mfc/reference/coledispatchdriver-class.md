---
title: Clase COleDispatchDriver | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchDriver class
- Automation clients, implementing Automation
- OLE dispatch interface
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
caps.latest.revision: 21
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 51fc2064e2f4b51b4f4328afb03920dab27ef74b
ms.lasthandoff: 02/24/2017

---
# <a name="coledispatchdriver-class"></a>Clase COleDispatchDriver
Implementa el cliente de automatización OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDispatchDriver  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|Construye un objeto `COleDispatchDriver`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Asocia un `IDispatch` conexión a la `COleDispatchDriver` objeto.|  
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Crea un `IDispatch` conexión y lo adjunta a la `COleDispatchDriver` objeto.|  
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Desasocia un `IDispatch` conexión sin liberarlo.|  
|[COleDispatchDriver:: GetProperty](#getproperty)|Obtiene una propiedad de automatización.|  
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Aplicación auxiliar para llamar a métodos de automatización.|  
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Versiones de un `IDispatch` conexión.|  
|[COleDispatchDriver:: SetProperty](#setproperty)|Establece una propiedad de automatización.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDispatchDriver::operator =](#operator_eq)|Copia el valor de origen en la `COleDispatchDriver` objeto.|  
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|Tiene acceso a la base de `IDispatch` puntero.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Especifica si se debe liberar el `IDispatch` durante `ReleaseDispatch` o la destrucción de objetos.|  
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Indica el puntero a la `IDispatch` interfaz se adjuntará a este `COleDispatchDriver`.|  
  
## <a name="remarks"></a>Comentarios  
 `COleDispatchDriver`no tiene una clase base.  
  
 Interfaces de envío OLE proporcionan acceso a los métodos y propiedades de un objeto. Las funciones miembro de `COleDispatchDriver` conectar, desconectar, crear y liberar una conexión de envío de tipo `IDispatch`. Otras funciones miembro utilizan listas de argumentos variables para simplificar la llamada **IDispatch:: Invoke**.  
  
 Se puede usar esta clase directamente, pero se utiliza generalmente sólo por clases creadas por el Asistente para agregar clases. Al crear nuevas clases de C++ mediante la importación de una biblioteca de tipos, se derivan de las nuevas clases `COleDispatchDriver`.  
  
 Para obtener más información sobre el uso de `COleDispatchDriver`, consulte los artículos siguientes:  
  
- [Clientes de automatización](../../mfc/automation-clients.md)  
  
- [Servidores de automatización](../../mfc/automation-servers.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `COleDispatchDriver`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="attachdispatch"></a>COleDispatchDriver::AttachDispatch  
 Llame a la función miembro `AttachDispatch` para adjuntar un puntero `IDispatch` al objeto `COleDispatchDriver` . Para obtener más información, consulte [implementa la interfaz IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
```  
void AttachDispatch(
        LPDISPATCH lpDispatch,  
        BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDispatch`  
 Puntero a un objeto `IDispatch` OLE que se adjuntará al objeto `COleDispatchDriver` .  
  
 `bAutoRelease`  
 Especifica si el envío se liberará cuando este objeto se salga del ámbito.  
  
### <a name="remarks"></a>Comentarios  
 Esta función libera cualquier puntero `IDispatch` que ya está conectado al objeto `COleDispatchDriver` .  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&3;](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]  
  
##  <a name="coledispatchdriver"></a>COleDispatchDriver::COleDispatchDriver  
 Construye un objeto `COleDispatchDriver`.  
  
```  
COleDispatchDriver();  
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);  
  COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDispatch`  
 Puntero a un objeto `IDispatch` OLE que se adjuntará al objeto `COleDispatchDriver` .  
  
 `bAutoRelease`  
 Especifica si el envío se liberará cuando este objeto se salga del ámbito.  
  
 `dispatchSrc`  
 Hacer referencia a un archivo `COleDispatchDriver` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El formulario `COleDispatchDriver`( `LPDISPATCH``lpDispatch`, **BOOL**`bAutoRelease` = **TRUE**) se conecta el [IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) interfaz.  
  
 El formulario `COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) copia existente `COleDispatchDriver` objeto e incrementa el recuento de referencias.  
  
 El formulario `COleDispatchDriver`() crea una `COleDispatchDriver` el objeto pero no se conecta el `IDispatch` interfaz. Antes de usar `COleDispatchDriver`() sin argumentos, debe conectar una `IDispatch` a él mediante [COleDispatchDriver::CreateDispatch](#createdispatch) o [COleDispatchDriver::AttachDispatch](#attachdispatch). Para obtener más información, consulte [implementa la interfaz IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](#createdispatch).  
  
##  <a name="createdispatch"></a>COleDispatchDriver::CreateDispatch  
 Crea un [IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) objeto de interfaz y se adjunta a la `COleDispatchDriver` objeto.  
  
```  
BOOL CreateDispatch(
        REFCLSID clsid,  
        COleException* pError = NULL);

 
BOOL CreateDispatch(
    LPCTSTR lpszProgID,  
    COleException* pError = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 Id. de clase del objeto de conexión `IDispatch` que se va a crear.  
  
 `pError`  
 Puntero a un objeto de excepción OLE, que contendrá el código de estado resultante de la creación.  
  
 `lpszProgID`  
 Puntero al identificador de programación (por ejemplo, "Excel.Document.5") del objeto de automatización para el que es necesario crear el objeto de envío.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero en caso de éxito; en caso contrario, es 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer Nº&4;](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]  
  
##  <a name="detachdispatch"></a>COleDispatchDriver::DetachDispatch  
 Desasocia actual `IDispatch` conexión de este objeto.  
  
```  
LPDISPATCH DetachDispatch();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la OLE adjuntado anteriormente `IDispatch` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `IDispatch` no se libera.  
  
 Para obtener más información acerca de la `LPDISPATCH` , vea [implementa la interfaz IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#5;](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]  
  
##  <a name="getproperty"></a>COleDispatchDriver:: GetProperty  
 Obtiene la propiedad del objeto especificada por `dwDispID`.  
  
```  
void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica la propiedad que se va a recuperar.  
  
 `vtProp`  
 Especifica la propiedad que se va a recuperar. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](#invokehelper).  
  
 `pvProp`  
 Dirección de la variable que recibirá el valor de propiedad. Debe coincidir con el tipo especificado por `vtProp`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer Nº&6;](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]  
  
##  <a name="invokehelper"></a>COleDispatchDriver::InvokeHelper  
 Llama a la propiedad o al método de objeto especificados por `dwDispID`, en el contexto especificado por `wFlags`.  
  
```  
void AFX_CDECL InvokeHelper(
        DISPID dwDispID,  
        WORD wFlags,  
        VARTYPE vtRet,  
        void* pvRet,  
        const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica el método o la propiedad que se va a invocar.  
  
 `wFlags`  
 Marcas que describen el contexto de la llamada a **IDispatch::Invoke**. . Para obtener una lista de valores posibles, vea el `wFlags` parámetro en [IDispatch:: Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `vtRet`  
 Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios.  
  
 `pvRet`  
 Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por `vtRet`.  
  
 `pbParamInfo`  
 Puntero a una cadena terminada en null de bytes que especifica los tipos de los parámetros que siguen a `pbParamInfo`.  
  
 *...*  
 Lista de variables de parámetros, de tipos especificados en `pbParamInfo`.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `pbParamInfo` especifica los tipos de los parámetros pasados al método o a la propiedad. La lista variable de argumentos se representa mediante **...** en la declaración de sintaxis.  
  
 Los valores posibles del argumento `vtRet` se toman de la enumeración `VARENUM` . Los valores posibles son los siguientes:  
  
|Símbolo|Tipo devuelto|  
|------------|-----------------|  
|`VT_EMPTY`|`void`|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**FECHA**|  
|`VT_BSTR`|`BSTR`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 El argumento `pbParamInfo` es una lista separada por espacios de constantes **VTS_** . Uno o varios de estos valores, separados por espacios (no por comas), especifican la lista de parámetros de la función. Los valores posibles se muestran con el [EVENT_CUSTOM](event-maps.md#event_custom) (macro).  
  
 Esta función convierte los parámetros a valores **VARIANTARG** y luego invoca el método [IDispatch:: Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx) . Si se produce un error en la llamada a `Invoke` , esta función generará una excepción. Si el `SCODE` (código de estado) devuelto por **IDispatch:: Invoke** es `DISP_E_EXCEPTION`, esta función lanza una [COleException](../../mfc/reference/coleexception-class.md) objeto; de lo contrario, produce una [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).  
  
 Para obtener más información, consulte [VARIANTARG](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118), [implementa la interfaz IDispatch](http://msdn.microsoft.com/library/windows/desktop/ms221037\(v=vs.85\).aspx), [IDispatch:: Invoke](http://msdn.microsoft.com/library/windows/desktop/ms221479\(v=vs.85\).aspx), y [estructura de códigos de Error COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](#createdispatch).  
  
##  <a name="m_bautorelease"></a>COleDispatchDriver::m_bAutoRelease  
 Si **TRUE**, el objeto COM acceso [m_lpDispatch](#m_lpdispatch) se se libera automáticamente cuando [ReleaseDispatch](#releasedispatch) se llama o cuando este `COleDispatchDriver` se destruye el objeto.  
  
```  
BOOL m_bAutoRelease;  
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `m_bAutoRelease` está establecido en **TRUE** en el constructor.  
  
 Para obtener más información sobre la liberación de objetos COM, consulte [implementa el recuento de referencias](http://msdn.microsoft.com/library/windows/desktop/ms693431) y [IUnknown:: Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#9;](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]  
  
##  <a name="m_lpdispatch"></a>COleDispatchDriver::m_lpDispatch  
 El puntero a la `IDispatch` interfaz se adjuntará a este `COleDispatchDriver`.  
  
```  
LPDISPATCH m_lpDispatch;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `m_lpDispatch` miembro de datos es una variable pública de tipo `LPDISPATCH`.  
  
 Para obtener más información, consulte [IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleDispatchDriver::AttachDispatch](#attachdispatch).  
  
##  <a name="operator_eq"></a>COleDispatchDriver::operator =  
 Copia el valor de origen en la `COleDispatchDriver` objeto.  
  
```  
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispatchSrc`  
 Un puntero a un `COleDispatchDriver` objeto.  
  
##  <a name="operator_lpdispatch"></a>COleDispatchDriver::operator LPDISPATCH  
 Tiene acceso a la base de `IDispatch` el puntero de la `COleDispatchDriver` objeto.  
  
```  
operator LPDISPATCH();
```   
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer Nº&8;](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]  
  
##  <a name="releasedispatch"></a>COleDispatchDriver::ReleaseDispatch  
 Versiones del `IDispatch` conexión. Para obtener más información, consulte [implementa la interfaz IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)  
  
```  
void ReleaseDispatch();
```  
  
### <a name="remarks"></a>Comentarios  
 Si se ha establecido la liberación automática para esta conexión, esta función llama a **IDispatch::Release** antes de liberar la interfaz.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [COleDispatchDriver::AttachDispatch](#attachdispatch).  
  
##  <a name="setproperty"></a>COleDispatchDriver:: SetProperty  
 Establece la propiedad del objeto OLE especificada por `dwDispID`.  
  
```  
void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica la propiedad que se va a establecer.  
  
 `vtProp`  
 Especifica el tipo de la propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](#invokehelper).  
  
 *...*  
 Un parámetro único del tipo especificado por `vtProp`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#7;](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo CALCDRIV de MFC](../../visual-cpp-samples.md)   
 [Ejemplo ACDUAL de MFC](../../visual-cpp-samples.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)

