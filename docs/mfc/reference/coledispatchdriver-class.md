---
title: Clase COleDispatchDriver
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
ms.openlocfilehash: 2b52ed3137a9a515278e018d69751aedaddb0cf1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753883"
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
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Asocia una `IDispatch` conexión `COleDispatchDriver` al objeto.|
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Crea `IDispatch` una conexión y la `COleDispatchDriver` adjunta al objeto.|
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Separa una `IDispatch` conexión, sin soltarla.|
|[COleDispatchDriver::GetProperty](#getproperty)|Obtiene una propiedad de automatización.|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Ayudante para llamar a métodos de automatización.|
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Libera `IDispatch` una conexión.|
|[COleDispatchDriver::SetProperty](#setproperty)|Establece una propiedad de automatización.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDispatchDriver::operator ?](#operator_eq)|Copia el valor `COleDispatchDriver` de origen en el objeto.|
|[COleDispatchDriver::operador LPDISPATCH](#operator_lpdispatch)|Tiene acceso al `IDispatch` puntero subyacente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Especifica si se `IDispatch` debe `ReleaseDispatch` liberar la destrucción durante o del objeto.|
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Indica el puntero `IDispatch` a la `COleDispatchDriver`interfaz adjunta a esto .|

## <a name="remarks"></a>Observaciones

`COleDispatchDriver`no tiene una clase base.

Las interfaces de envío OLE proporcionan acceso a los métodos y propiedades de un objeto. Funciones `COleDispatchDriver` miembro de adjuntar, separar, crear y `IDispatch`liberar una conexión de envío de tipo . Otras funciones miembro utilizan listas `IDispatch::Invoke`de argumentos variables para simplificar la llamada.

Esta clase se puede usar directamente, pero generalmente solo la usan las clases creadas por el Asistente para agregar clases. Al crear nuevas clases C++ importando una biblioteca de `COleDispatchDriver`tipos, las nuevas clases se derivan de .

Para obtener más `COleDispatchDriver`información sobre el uso de , consulte los siguientes artículos:

- [Clientes de automatización](../../mfc/automation-clients.md)

- [Servidores de automatización](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`COleDispatchDriver`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a>COleDispatchDriver::AttachDispatch

Llame a la función miembro `AttachDispatch` para adjuntar un puntero `IDispatch` al objeto `COleDispatchDriver` . Para obtener más información, consulta [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```cpp
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

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a>COleDispatchDriver::COleDispatchDriver

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
Referencia a `COleDispatchDriver` un objeto existente.

### <a name="remarks"></a>Observaciones

El `COleDispatchDriver`formulario `LPDISPATCH lpDispatch`( , **BOOL**`bAutoRelease` = **TRUE**) conecta la interfaz [IDispatch.](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

El `COleDispatchDriver`formulario ( **const**`COleDispatchDriver`& `dispatchSrc` `COleDispatchDriver` ) copia un objeto existente e incrementa el recuento de referencias.

El `COleDispatchDriver`formulario ( `COleDispatchDriver` ) crea un `IDispatch` objeto pero no conecta la interfaz. Antes `COleDispatchDriver`de usar ( ) sin `IDispatch` argumentos, debe conectarse a él mediante [COleDispatchDriver::CreateDispatch](#createdispatch) o [COleDispatchDriver::AttachDispatch](#attachdispatch). Para obtener más información, consulta [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a>COleDispatchDriver::CreateDispatch

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

*clsid*<br/>
Id. de clase del objeto de conexión `IDispatch` que se va a crear.

*pError*<br/>
Puntero a un objeto de excepción OLE, que contendrá el código de estado resultante de la creación.

*lpszProgID*<br/>
Puntero al identificador de programación (por ejemplo, "Excel.Document.5") del objeto de automatización para el que es necesario crear el objeto de envío.

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a>COleDispatchDriver::DetachDispatch

Separa la `IDispatch` conexión actual de este objeto.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto OLE `IDispatch` previamente asociado.

### <a name="remarks"></a>Observaciones

El `IDispatch` no se libera.

Para obtener más información acerca del tipo LPDISPATCH, vea [Implementar la interfaz IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a>COleDispatchDriver::GetProperty

Obtiene la propiedad de objeto especificada por *dwDispID*.

```cpp
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

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a>COleDispatchDriver::InvokeHelper

Llama al método o propiedad de objeto especificado por *dwDispID*, en el contexto especificado por *wFlags*.

```cpp
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
Indicadores que describen el `IDispatch::Invoke`contexto de la llamada a . . Para obtener una lista de valores posibles, vea el *wFlags* parámetro en [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) en el Windows SDK.

*vtRet*<br/>
Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios.

*pvRet*<br/>
Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por *vtRet*.

*pbParamInfo*<br/>
Puntero a una cadena de bytes terminada en null que especifica los tipos de los parámetros siguientes *pbParamInfo*.

*...*<br/>
Lista variable de parámetros, de tipos especificados en *pbParamInfo*.

### <a name="remarks"></a>Observaciones

El parámetro *pbParamInfo* especifica los tipos de los parámetros pasados al método o propiedad. La lista variable de argumentos se representa mediante **...** en la declaración de sintaxis.

Los valores posibles para el argumento *vtRet* se toman de la enumeración VARENUM. Los valores posibles son los siguientes:

|Símbolo|Tipo de valor devuelto|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**Fecha**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**BOOL**|
|VT_VARIANT|**Variante**|
|VT_UNKNOWN|LPUNKNOWN|

El argumento *pbParamInfo* es una lista separada por espacios de **VTS_** constantes. Uno o varios de estos valores, separados por espacios (no por comas), especifican la lista de parámetros de la función. Los valores posibles se muestran con la macro [EVENT_CUSTOM](event-maps.md#event_custom) .

Esta función convierte los parámetros a valores VARIANTARG y luego invoca el método [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) . Si se produce un error en la llamada a `Invoke` , esta función generará una excepción. Si el SCODE (código `IDispatch::Invoke` de estado) devuelto por es DISP_E_EXCEPTION, esta función produce un [COleException](../../mfc/reference/coleexception-class.md) objeto; de lo contrario, lanza una [excepción COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Para obtener más información, vea [VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant), Implementación de [la interfaz IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)y [Estructura de](/windows/win32/com/structure-of-com-error-codes) códigos de error COM en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a>COleDispatchDriver::m_bAutoRelease

Si es TRUE, el objeto COM al que tiene acceso `COleDispatchDriver` [m_lpDispatch](#m_lpdispatch) se liberará automáticamente cuando se llame a [ReleaseDispatch](#releasedispatch) o cuando se destruya este objeto.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Observaciones

De forma `m_bAutoRelease` predeterminada, se establece en TRUE en el constructor.

Para obtener más información sobre cómo liberar objetos COM, vea [Implementación](/windows/win32/com/implementing-reference-counting) de recuento de referencias e [IUnknown::Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a>COleDispatchDriver::m_lpDispatch

El puntero `IDispatch` a la `COleDispatchDriver`interfaz adjunta a esto .

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Observaciones

El `m_lpDispatch` miembro de datos es una variable pública de tipo LPDISPATCH.

Para obtener más información, consulte [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::AttachDispatch](#attachdispatch).

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a>COleDispatchDriver::operator ?

Copia el valor `COleDispatchDriver` de origen en el objeto.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Parámetros

*dispatchSrc*<br/>
Puntero a un `COleDispatchDriver` objeto existente.

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a>COleDispatchDriver::operador LPDISPATCH

Tiene acceso al `IDispatch` puntero `COleDispatchDriver` subyacente del objeto.

```
operator LPDISPATCH();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a>COleDispatchDriver::ReleaseDispatch

Libera `IDispatch` la conexión. Para obtener más información, consulte [Implementación de la interfaz IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```cpp
void ReleaseDispatch();
```

### <a name="remarks"></a>Observaciones

Si se ha establecido la versión `IDispatch::Release` automática para esta conexión, esta función llama antes de liberar la interfaz.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::AttachDispatch](#attachdispatch).

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a>COleDispatchDriver::SetProperty

Establece la propiedad de objeto OLE especificada por *dwDispID*.

```cpp
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
Un único parámetro del tipo especificado por *vtProp*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
