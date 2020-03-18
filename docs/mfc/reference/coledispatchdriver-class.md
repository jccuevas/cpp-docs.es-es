---
title: COleDispatchDriver (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: fa88147b57b0506f7f9ab96d4a5d2f43fdd75458
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426634"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver (clase)

Implementa el cliente de automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleDispatchDriver
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDispatchDriver:: COleDispatchDriver](#coledispatchdriver)|Construye un objeto `COleDispatchDriver`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDispatchDriver:: AttachDispatch](#attachdispatch)|Asocia una conexión `IDispatch` al objeto `COleDispatchDriver`.|
|[COleDispatchDriver:: CreateDispatch](#createdispatch)|Crea una conexión `IDispatch` y la adjunta al objeto `COleDispatchDriver`.|
|[COleDispatchDriver::D etachDispatch](#detachdispatch)|Desasocia una conexión `IDispatch`, sin liberarla.|
|[COleDispatchDriver:: GetProperty](#getproperty)|Obtiene una propiedad de automatización.|
|[COleDispatchDriver:: InvokeHelper](#invokehelper)|Aplicación auxiliar para llamar a métodos de automatización.|
|[COleDispatchDriver:: ReleaseDispatch](#releasedispatch)|Libera una conexión `IDispatch`.|
|[COleDispatchDriver:: SetProperty](#setproperty)|Establece una propiedad de automatización.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDispatchDriver:: Operator =](#operator_eq)|Copia el valor de origen en el objeto `COleDispatchDriver`.|
|[COleDispatchDriver:: Operator LPDISPATCH](#operator_lpdispatch)|Obtiene acceso al puntero de `IDispatch` subyacente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDispatchDriver:: m_bAutoRelease](#m_bautorelease)|Especifica si se va a liberar el `IDispatch` durante la destrucción de `ReleaseDispatch` o del objeto.|
|[COleDispatchDriver:: m_lpDispatch](#m_lpdispatch)|Indica el puntero a la interfaz `IDispatch` asociada a este `COleDispatchDriver`.|

## <a name="remarks"></a>Observaciones

`COleDispatchDriver` no tiene una clase base.

Las interfaces de envío OLE proporcionan acceso a los métodos y propiedades de un objeto. Las funciones miembro de `COleDispatchDriver` adjuntar, separar, crear y liberar una conexión de envío de tipo `IDispatch`. Otras funciones miembro utilizan listas de argumentos variables para simplificar la llamada a `IDispatch::Invoke`.

Esta clase se puede usar directamente, pero solo se usa en las clases creadas por el Asistente para agregar clases. Al crear nuevas C++ clases mediante la importación de una biblioteca de tipos, las nuevas clases se derivan de `COleDispatchDriver`.

Para obtener más información sobre el uso de `COleDispatchDriver`, consulte los siguientes artículos:

- [Automation Clients](../../mfc/automation-clients.md)

- [Servidores de automatización](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`COleDispatchDriver`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="attachdispatch"></a>COleDispatchDriver:: AttachDispatch

Llame a la función miembro `AttachDispatch` para adjuntar un puntero `IDispatch` al objeto `COleDispatchDriver` . Para obtener más información, consulta [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

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

### <a name="remarks"></a>Observaciones

Esta función libera cualquier puntero `IDispatch` que ya está conectado al objeto `COleDispatchDriver` .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

##  <a name="coledispatchdriver"></a>COleDispatchDriver:: COleDispatchDriver

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
Referencia a un objeto de `COleDispatchDriver` existente.

### <a name="remarks"></a>Observaciones

El formulario `COleDispatchDriver`(`LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **true**) conecta la interfaz [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) .

El formulario `COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) copia un objeto `COleDispatchDriver` existente e incrementa el recuento de referencias.

El formulario `COleDispatchDriver`() crea un objeto `COleDispatchDriver` pero no conecta la interfaz `IDispatch`. Antes de usar `COleDispatchDriver`() sin argumentos, debe conectar una `IDispatch` a ella mediante [COleDispatchDriver:: CreateDispatch](#createdispatch) o [COleDispatchDriver:: AttachDispatch](#attachdispatch). Para obtener más información, consulta [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](#createdispatch).

##  <a name="createdispatch"></a>COleDispatchDriver:: CreateDispatch

Crea un objeto de interfaz [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) y lo vincula al objeto `COleDispatchDriver` .

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

##  <a name="detachdispatch"></a>COleDispatchDriver::D etachDispatch

Desasocia la conexión `IDispatch` actual de este objeto.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto OLE `IDispatch` asociado previamente.

### <a name="remarks"></a>Observaciones

No se libera el `IDispatch`.

Para obtener más información sobre el tipo LPDISPATCH, consulte [implementación de la interfaz IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

##  <a name="getproperty"></a>COleDispatchDriver:: GetProperty

Obtiene la propiedad de objeto especificada por *dwDispID*.

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
Especifica la propiedad que se va a recuperar. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](#invokehelper).

*pvProp*<br/>
Dirección de la variable que recibirá el valor de propiedad. Debe coincidir con el tipo especificado por *vtProp*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

##  <a name="invokehelper"></a>COleDispatchDriver:: InvokeHelper

Llama al método de objeto o a la propiedad especificada por *dwDispID*, en el contexto especificado por *wFlags*.

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
Marcas que describen el contexto de la llamada a `IDispatch::Invoke`. . Para obtener una lista de los valores posibles, vea el parámetro *wFlags* en [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) en el Windows SDK.

*vtRet*<br/>
Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios.

*pvRet*<br/>
Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por *vtRet*.

*pbParamInfo*<br/>
Puntero a una cadena terminada en NULL de bytes que especifica los tipos de los parámetros que siguen a *pbParamInfo*.

*...*<br/>
Lista de variables de parámetros, de tipos especificados en *pbParamInfo*.

### <a name="remarks"></a>Observaciones

El parámetro *pbParamInfo* especifica los tipos de los parámetros pasados al método o a la propiedad. La lista variable de argumentos se representa mediante **...** en la declaración de sintaxis.

Los valores posibles para el argumento *vtRet* se toman de la enumeración VARENUM. Los valores posibles son los siguientes:

|Símbolo|Tipo de valor devuelto|
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
|VT_VARIANT|**VARIANTE**|
|VT_UNKNOWN|LPUNKNOWN|

El argumento *pbParamInfo* es una lista separada por espacios de constantes de **VTS_** . Uno o varios de estos valores, separados por espacios (no por comas), especifican la lista de parámetros de la función. Los valores posibles se muestran con la macro [EVENT_CUSTOM](event-maps.md#event_custom) .

Esta función convierte los parámetros a valores VARIANTARG y luego invoca el método [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) . Si se produce un error en la llamada a `Invoke` , esta función generará una excepción. Si el SCODE (código de estado) devuelto por `IDispatch::Invoke` es DISP_E_EXCEPTION, esta función produce un objeto [COleException](../../mfc/reference/coleexception-class.md) . en caso contrario, se produce una [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Para obtener más información, vea [VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant), [implementar la interfaz IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)y [estructura de códigos de error com](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](#createdispatch).

##  <a name="m_bautorelease"></a>COleDispatchDriver:: m_bAutoRelease

Si es TRUE, el objeto COM al que tiene acceso [m_lpDispatch](#m_lpdispatch) se liberará automáticamente cuando se llame a [ReleaseDispatch](#releasedispatch) o cuando se destruya este objeto `COleDispatchDriver`.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, `m_bAutoRelease` se establece en TRUE en el constructor.

Para obtener más información sobre la liberación de objetos COM, vea [implementar el recuento de referencias](/windows/win32/com/implementing-reference-counting) e [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

##  <a name="m_lpdispatch"></a>COleDispatchDriver:: m_lpDispatch

Puntero a la interfaz de `IDispatch` asociada a este `COleDispatchDriver`.

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Observaciones

El miembro de datos `m_lpDispatch` es una variable pública de tipo LPDISPATCH.

Para obtener más información, vea [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver:: AttachDispatch](#attachdispatch).

##  <a name="operator_eq"></a>COleDispatchDriver:: Operator =

Copia el valor de origen en el objeto `COleDispatchDriver`.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parámetros

*dispatchSrc*<br/>
Puntero a un objeto de `COleDispatchDriver` existente.

##  <a name="operator_lpdispatch"></a>COleDispatchDriver:: Operator LPDISPATCH

Obtiene acceso al puntero de `IDispatch` subyacente del objeto `COleDispatchDriver`.

```
operator LPDISPATCH();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

##  <a name="releasedispatch"></a>COleDispatchDriver:: ReleaseDispatch

Libera la conexión de `IDispatch`. Para obtener más información, consulte [implementación de la interfaz IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) .

```
void ReleaseDispatch();
```

### <a name="remarks"></a>Observaciones

Si se ha establecido la versión automática para esta conexión, esta función llama a `IDispatch::Release` antes de liberar la interfaz.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver:: AttachDispatch](#attachdispatch).

##  <a name="setproperty"></a>COleDispatchDriver:: SetProperty

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
Especifica el tipo de la propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](#invokehelper).

*...*<br/>
Un parámetro único del tipo especificado por *vtProp*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo ACDUAL de MFC](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
