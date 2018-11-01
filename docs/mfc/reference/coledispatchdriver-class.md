---
title: COleDispatchDriver (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- COleDispatchDriver [MFC], COleDispatchDriver
- COleDispatchDriver [MFC], AttachDispatch
- COleDispatchDriver [MFC], CreateDispatch
- COleDispatchDriver [MFC], DetachDispatch
- COleDispatchDriver [MFC], GetProperty
- COleDispatchDriver [MFC], InvokeHelper
- COleDispatchDriver [MFC], ReleaseDispatch
- COleDispatchDriver [MFC], SetProperty
- COleDispatchDriver [MFC], m_bAutoRelease
- COleDispatchDriver [MFC], m_lpDispatch
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da7093d25e8221ce3fc3ec8d0d13f8bbc5b420d2
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821327"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver (clase)

Implementa el cliente de automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleDispatchDriver
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|Construye un objeto `COleDispatchDriver`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Asocia un `IDispatch` conexión a la `COleDispatchDriver` objeto.|
|[COleDispatchDriver:: CreateDispatch](#createdispatch)|Crea un `IDispatch` conexión y lo asocia a la `COleDispatchDriver` objeto.|
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Desasocia un `IDispatch` conexión sin liberarlo.|
|[COleDispatchDriver:: GetProperty](#getproperty)|Obtiene una propiedad de automatización.|
|[COleDispatchDriver:: Invokehelper](#invokehelper)|Aplicación auxiliar para llamar a métodos de automatización.|
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Las versiones un `IDispatch` conexión.|
|[COleDispatchDriver:: SetProperty](#setproperty)|Establece una propiedad de automatización.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[COleDispatchDriver::operator =](#operator_eq)|Copia el valor de origen en el `COleDispatchDriver` objeto.|
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|Tiene acceso a subyacente `IDispatch` puntero.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Especifica si se debe liberar el `IDispatch` durante `ReleaseDispatch` o destrucción de objetos.|
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Indica el puntero a la `IDispatch` interfaz asociada a este `COleDispatchDriver`.|

## <a name="remarks"></a>Comentarios

`COleDispatchDriver` no tiene una clase base.

Interfaces de envío OLE proporcionan acceso a los métodos y propiedades de un objeto. Las funciones miembro de `COleDispatchDriver` adjuntar, separar, crear y liberar una conexión de envío de tipo `IDispatch`. Otras funciones miembro usan listas de argumentos variables para simplificar la llamada `IDispatch::Invoke`.

Esta clase puede utilizarse directamente, pero generalmente es utilizado únicamente por las clases creadas por el Asistente para agregar clases. Al crear nuevas clases de C++ mediante la importación de una biblioteca de tipos, las nuevas clases se derivan `COleDispatchDriver`.

Para obtener más información sobre el uso de `COleDispatchDriver`, consulte los artículos siguientes:

- [Clientes de automatización](../../mfc/automation-clients.md)

- [Servidores de automatización](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`COleDispatchDriver`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="attachdispatch"></a>  COleDispatchDriver::AttachDispatch

Llame a la función miembro `AttachDispatch` para adjuntar un puntero `IDispatch` al objeto `COleDispatchDriver` . Para obtener más información, consulte [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpDispatch*<br/>
Puntero a un objeto `IDispatch` OLE que se adjuntará al objeto `COleDispatchDriver` .

*bAutoRelease*<br/>
Especifica si el envío se liberará cuando este objeto se salga del ámbito.

### <a name="remarks"></a>Comentarios

Esta función libera cualquier puntero `IDispatch` que ya está conectado al objeto `COleDispatchDriver` .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

##  <a name="coledispatchdriver"></a>  COleDispatchDriver::COleDispatchDriver

Construye un objeto `COleDispatchDriver`.

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parámetros

*lpDispatch*<br/>
Puntero a un objeto `IDispatch` OLE que se adjuntará al objeto `COleDispatchDriver` .

*bAutoRelease*<br/>
Especifica si el envío se liberará cuando este objeto se salga del ámbito.

*dispatchSrc*<br/>
Hacer referencia a un `COleDispatchDriver` objeto.

### <a name="remarks"></a>Comentarios

El formulario `COleDispatchDriver`( `LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **TRUE**) se conecta el [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) interfaz.

El formulario `COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) copia existente `COleDispatchDriver` objeto e incrementa el recuento de referencias.

El formulario `COleDispatchDriver`() se crea un `COleDispatchDriver` objeto pero no se conecta el `IDispatch` interfaz. Antes de usar `COleDispatchDriver`() sin argumentos, debe conectar un `IDispatch` a él mediante [COleDispatchDriver:: CreateDispatch](#createdispatch) o [COleDispatchDriver::AttachDispatch](#attachdispatch). Para obtener más información, consulte [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver:: CreateDispatch](#createdispatch).

##  <a name="createdispatch"></a>  COleDispatchDriver:: CreateDispatch

Crea un [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) objeto de interfaz y se adjunta a la `COleDispatchDriver` objeto.

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*CLSID*<br/>
Id. de clase del objeto de conexión `IDispatch` que se va a crear.

*pError*<br/>
Puntero a un objeto de excepción OLE, que contendrá el código de estado resultante de la creación.

*lpszProgID*<br/>
Puntero al identificador de programación (por ejemplo, "Excel.Document.5") del objeto de automatización para el que es necesario crear el objeto de envío.

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

##  <a name="detachdispatch"></a>  COleDispatchDriver::DetachDispatch

Desasocia actual `IDispatch` conexión de este objeto.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la OLE adjunta anteriormente `IDispatch` objeto.

### <a name="remarks"></a>Comentarios

El `IDispatch` no se libera.

Para obtener más información sobre el tipo LPDISPATCH, consulte [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

##  <a name="getproperty"></a>  COleDispatchDriver:: GetProperty

Obtiene la propiedad del objeto especificada por *dwDispID*.

```
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica la propiedad que se va a recuperar.

*vtProp*<br/>
Especifica la propiedad que se va a recuperar. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver:: Invokehelper](#invokehelper).

*pvProp*<br/>
Dirección de la variable que recibirá el valor de propiedad. Debe coincidir con el tipo especificado por *vtProp*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

##  <a name="invokehelper"></a>  COleDispatchDriver:: Invokehelper

Llama al método de objeto o la propiedad especificada por *dwDispID*, en el contexto especificado por *wFlags*.

```
void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el método o la propiedad que se va a invocar.

*wFlags*<br/>
Marcas que describen el contexto de la llamada a `IDispatch::Invoke`. . Para obtener una lista de valores posibles, vea el *wFlags* parámetro [IDispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) en el SDK de Windows.

*vtRet*<br/>
Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios.

*pvRet*<br/>
Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por *vtRet*.

*pbParamInfo*<br/>
Puntero a una cadena terminada en null de bytes que especifica los tipos de los parámetros que siguen *pbParamInfo*.

*...*<br/>
Lista de variables de parámetros de tipos especificados en *pbParamInfo*.

### <a name="remarks"></a>Comentarios

El *pbParamInfo* parámetro especifica los tipos de los parámetros pasados al método o propiedad. La lista variable de argumentos se representa mediante **...** en la declaración de sintaxis.

Los valores posibles para el *vtRet* argumento se toman de la enumeración VARENUM. Los valores posibles son los siguientes:

|Símbolo|Tipo devuelto|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**DATE**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**BOOL**|
|VT_VARIANT|**VARIANT**|
|VT_UNKNOWN|LPUNKNOWN|

El *pbParamInfo* argumento es una lista separada por espacios de **VTS_** constantes. Uno o varios de estos valores, separados por espacios (no por comas), especifican la lista de parámetros de la función. Los valores posibles se muestran con el [EVENT_CUSTOM](event-maps.md#event_custom) macro.

Esta función convierte los parámetros con valores VARIANTARG y luego invoca el [IDispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) método. Si se produce un error en la llamada a `Invoke` , esta función generará una excepción. Si el SCODE (código de estado) devuelto por `IDispatch::Invoke` es DISP_E_EXCEPTION, esta función genera un [COleException](../../mfc/reference/coleexception-class.md) objeto; de lo contrario, genera un [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Para obtener más información, consulte [VARIANTARG](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke), y [estructura de códigos de Error COM](/windows/desktop/com/structure-of-com-error-codes) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver:: CreateDispatch](#createdispatch).

##  <a name="m_bautorelease"></a>  COleDispatchDriver::m_bAutoRelease

Si es TRUE, obtiene acceso al objeto COM por [m_lpDispatch](#m_lpdispatch) se automáticamente publicará cuando [ReleaseDispatch](#releasedispatch) se denomina o cuando este `COleDispatchDriver` se destruye el objeto.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, `m_bAutoRelease` está establecida en TRUE en el constructor.

Para obtener más información sobre la liberación de objetos COM, vea [implementa el recuento de referencias](/windows/desktop/com/implementing-reference-counting) y [IUnknown:: Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

##  <a name="m_lpdispatch"></a>  COleDispatchDriver::m_lpDispatch

El puntero a la `IDispatch` interfaz asociada a este `COleDispatchDriver`.

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Comentarios

El `m_lpDispatch` miembro de datos es una variable pública de tipo LPDISPATCH.

Para obtener más información, consulte [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::AttachDispatch](#attachdispatch).

##  <a name="operator_eq"></a>  COleDispatchDriver::operator =

Copia el valor de origen en el `COleDispatchDriver` objeto.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parámetros

*dispatchSrc*<br/>
Un puntero a una existente `COleDispatchDriver` objeto.

##  <a name="operator_lpdispatch"></a>  COleDispatchDriver::operator LPDISPATCH

Tiene acceso a subyacente `IDispatch` puntero de la `COleDispatchDriver` objeto.

```
operator LPDISPATCH();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

##  <a name="releasedispatch"></a>  COleDispatchDriver::ReleaseDispatch

Las versiones del `IDispatch` conexión. Para obtener más información, consulte [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```
void ReleaseDispatch();
```

### <a name="remarks"></a>Comentarios

Si se ha establecido la liberación automática para esta conexión, esta función llama a `IDispatch::Release` antes de liberar la interfaz.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::AttachDispatch](#attachdispatch).

##  <a name="setproperty"></a>  COleDispatchDriver:: SetProperty

Establece la propiedad del objeto OLE especificada por *dwDispID*.

```
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica la propiedad que se va a establecer.

*vtProp*<br/>
Especifica el tipo de la propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver:: Invokehelper](#invokehelper).

*...*<br/>
Un único parámetro del tipo especificado por *vtProp*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CALCDRIV](../../visual-cpp-samples.md)<br/>
[Ejemplo ACDUAL de MFC](../../visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
