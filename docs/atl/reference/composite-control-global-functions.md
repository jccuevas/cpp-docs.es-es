---
title: Funciones globales de control compuesto
ms.date: 11/04/2016
f1_keywords:
- atlhost/ATL::AtlAxDialogBox
- atlhost/ATL::AtlAxCreateDialog
- atlhost/ATL::AtlAxCreateControl
- atlhost/ATL::AtlAxCreateControlEx
- atlhost/ATL::AtlAxCreateControlLic
- atlhost/ATL::AtlAxCreateControlLicEx
- atlhost/ATL::AtlAxAttachControl
- atlhost/ATL::AtlAxGetHost
- atlhost/ATL::AtlAxGetControl
- atlhost/ATL::AtlSetChildSite
- atlhost/ATL::AtlAxWinInit
- atlhost/ATL::AtlAxWinTerm
- atlhost/ATL::AtlGetObjectSourceInterface
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
ms.openlocfilehash: 525fc01247053a1e2bc993398978cb332262a1a5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864766"
---
# <a name="composite-control-global-functions"></a>Funciones globales de control compuesto

Estas funciones proporcionan compatibilidad para crear cuadros de diálogo y para crear, hospedar y conceder licencias a controles ActiveX.

> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|Crea un cuadro de diálogo modal a partir de una plantilla de cuadros de diálogo proporcionada por el usuario. El cuadro de diálogo resultante puede contener controles ActiveX.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Crea un cuadro de diálogo no modal a partir de una plantilla de cuadros de diálogo proporcionada por el usuario. El cuadro de diálogo resultante puede contener controles ActiveX.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Crea un control ActiveX, lo inicializa, lo hospeda en la ventana especificada y recupera un puntero de interfaz (o punteros) del control.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Crea un control ActiveX con licencia, lo inicializa, lo hospeda en la ventana especificada y recupera un puntero de interfaz (o punteros) del control.|
|[AtlAxAttachControl](#atlaxattachcontrol)|Asocia un control creado previamente con la ventana especificada.|
|[AtlAxGetHost](#atlaxgethost)|Se usa para obtener un puntero de interfaz directo al contenedor para una ventana especificada (si existe), dado su identificador.|
|[AtlAxGetControl](#atlaxgetcontrol)|Se utiliza para obtener un puntero de interfaz directo al control contenido dentro de una ventana especificada (si existe), dado su identificador.|
|[AtlSetChildSite](#atlsetchildsite)|Inicializa el `IUnknown` del sitio secundario.|
|[AtlAxWinInit](#atlaxwininit)|Inicializa el código de hospedaje para los objetos AxWin.|
|[AtlAxWinTerm](#atlaxwinterm)|Desinicializa el código de hospedaje para los objetos AxWin.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Devuelve información sobre la interfaz de origen predeterminada de un objeto.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlhost. h

##  <a name="atlaxdialogbox"></a>AtlAxDialogBox

Crea un cuadro de diálogo modal a partir de una plantilla de cuadros de diálogo proporcionada por el usuario.

```
ATLAPI_(int) AtlAxDialogBox(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
de Identifica una instancia del módulo cuyo archivo ejecutable contiene la plantilla de cuadro de diálogo.

*lpTemplateName*<br/>
de Identifica la plantilla de cuadro de diálogo. Este parámetro es el puntero a una cadena de caracteres terminada en null que especifica el nombre de la plantilla de cuadro de diálogo o un valor entero que especifica el identificador de recursos de la plantilla de cuadro de diálogo. Si el parámetro especifica un identificador de recursos, su palabra de orden superior debe ser cero y su palabra de orden inferior debe contener el identificador. Puede usar la macro [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) para crear este valor.

*hWndParent*<br/>
de Identifica la ventana que posee el cuadro de diálogo.

*lpDialogProc*<br/>
de Apunta al procedimiento del cuadro de diálogo. Para obtener más información sobre el procedimiento de cuadro de diálogo, vea [función dialogproc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
de Especifica el valor que se va a pasar al cuadro de diálogo en el parámetro *lParam* del mensaje de WM_INITDIALOG.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Para usar `AtlAxDialogBox` con una plantilla de cuadro de diálogo que contenga un control ActiveX, especifique un CLSID, APPID o cadena de dirección URL válidos como el campo de *texto* de la sección de **control** del recurso de cuadro de diálogo, junto con "AtlAxWin80" como campo de *nombre de clase* en la misma sección. A continuación se muestra el aspecto que podría tener una sección de **control** válida:

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

Para obtener más información sobre la edición de scripts de recursos, consulte [Cómo: abrir un archivo de script de recursos en formato de texto](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Para obtener más información sobre el control de las instrucciones de definición de recursos, vea [parámetros de control comunes](/windows/win32/menurc/common-control-parameters) en Windows SDK: SDK Tools.

Para obtener más información sobre los cuadros de diálogo en general, consulte [DialogBox](/windows/win32/api/winuser/nf-winuser-dialogboxw) y [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) en el Windows SDK.

##  <a name="atlaxcreatedialog"></a>AtlAxCreateDialog

Crea un cuadro de diálogo no modal a partir de una plantilla de cuadros de diálogo proporcionada por el usuario.

```
ATLAPI_(HWND) AtlAxCreateDialog(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>Parámetros

*hInstance*<br/>
de Identifica una instancia del módulo cuyo archivo ejecutable contiene la plantilla de cuadro de diálogo.

*lpTemplateName*<br/>
de Identifica la plantilla de cuadro de diálogo. Este parámetro es el puntero a una cadena de caracteres terminada en null que especifica el nombre de la plantilla de cuadro de diálogo o un valor entero que especifica el identificador de recursos de la plantilla de cuadro de diálogo. Si el parámetro especifica un identificador de recursos, su palabra de orden superior debe ser cero y su palabra de orden inferior debe contener el identificador. Puede usar la macro [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) para crear este valor.

*hWndParent*<br/>
de Identifica la ventana que posee el cuadro de diálogo.

*lpDialogProc*<br/>
de Apunta al procedimiento del cuadro de diálogo. Para obtener más información sobre el procedimiento de cuadro de diálogo, vea [función dialogproc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
de Especifica el valor que se va a pasar al cuadro de diálogo en el parámetro *lParam* del mensaje de WM_INITDIALOG.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

El cuadro de diálogo resultante puede contener controles ActiveX.

Consulte [CreateDialog](/windows/win32/api/winuser/nf-winuser-createdialogw) y [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) en el Windows SDK.

##  <a name="atlaxcreatecontrol"></a>AtlAxCreateControl

Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada.

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una cadena que se va a pasar al control. Debe tener el formato de una de las siguientes maneras:

- Un ProgID como `"MSCAL.Calendar.7"`

- Un CLSID como `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una dirección URL como `"<https://www.microsoft.com>"`

- Referencia a un documento activo como `"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` debe preceder al fragmento HTML para que se designe como una secuencia de MSHTML.

*hWnd*<br/>
de Identificador de la ventana a la que se asociará el control.

*pStream*<br/>
de Un puntero a un flujo que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
enuncia La dirección de un puntero que recibirá el `IUnknown` del contenedor. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta función global proporciona el mismo resultado que llamar a [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *hWnd*, *pStream*, null, null, null, null);.

Para crear un control ActiveX con licencia, vea [AtlAxCreateControlLic](#atlaxcreatecontrollic).

##  <a name="atlaxcreatecontrolex"></a>AtlAxCreateControlEx

Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada. También se puede crear un puntero de interfaz y un receptor de eventos para el nuevo control.

```
ATLAPI AtlAxCreateControlEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una cadena que se va a pasar al control. Debe tener el formato de una de las siguientes maneras:

- Un ProgID como `"MSCAL.Calendar.7"`

- Un CLSID como `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una dirección URL como `"<https://www.microsoft.com>"`

- Referencia a un documento activo como `"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` debe preceder al fragmento HTML para que se designe como una secuencia de MSHTML.

*hWnd*<br/>
de Identificador de la ventana a la que se asociará el control.

*pStream*<br/>
de Un puntero a un flujo que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
enuncia La dirección de un puntero que recibirá el `IUnknown` del contenedor. Puede ser NULL.

*ppUnkControl*<br/>
enuncia Dirección de un puntero que recibirá el `IUnknown` del control creado. Puede ser NULL.

*iidSink*<br/>
Identificador de interfaz de una interfaz de salida en el objeto contenido.

*punkSink*<br/>
Puntero a la interfaz `IUnknown` del objeto receptor que se va a conectar al punto de conexión especificado por *iidSink* en el objeto contenido después de que el objeto contenido se haya creado correctamente.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

`AtlAxCreateControlEx` es similar a [AtlAxCreateControl](#atlaxcreatecontrol) , pero también permite recibir un puntero de interfaz al control recién creado y configurar un receptor de eventos para recibir los eventos desencadenados por el control.

Para crear un control ActiveX con licencia, vea [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).

##  <a name="atlaxcreatecontrollic"></a>AtlAxCreateControlLic

Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada.

```
ATLAPI AtlAxCreateControlLic(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una cadena que se va a pasar al control. Debe tener el formato de una de las siguientes maneras:

- Un ProgID como `"MSCAL.Calendar.7"`

- Un CLSID como `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una dirección URL como `"<https://www.microsoft.com>"`

- Referencia a un documento activo como `"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` debe preceder al fragmento HTML para que se designe como una secuencia de MSHTML.

*hWnd*<br/>
Identificador de la ventana a la que se asociará el control.

*pStream*<br/>
Un puntero a un flujo que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
La dirección de un puntero que recibirá el `IUnknown` del contenedor. Puede ser NULL.

*bstrLic*<br/>
BSTR que contiene la licencia para el control.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="example"></a>Ejemplo

Vea [hospedar controles ActiveX mediante](../../atl/hosting-activex-controls-using-atl-axhost.md) el método AXHOST de ATL para obtener un ejemplo de cómo utilizar `AtlAxCreateControlLic`.

##  <a name="atlaxcreatecontrollicex"></a>AtlAxCreateControlLicEx

Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada. También se puede crear un puntero de interfaz y un receptor de eventos para el nuevo control.

```
ATLAPI AtlAxCreateControlLicEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Puntero a una cadena que se va a pasar al control. Debe tener el formato de una de las siguientes maneras:

- Un ProgID como `"MSCAL.Calendar.7"`

- Un CLSID como `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una dirección URL como `"<https://www.microsoft.com>"`

- Referencia a un documento activo como `"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` debe preceder al fragmento HTML para que se designe como una secuencia de MSHTML.

*hWnd*<br/>
Identificador de la ventana a la que se asociará el control.

*pStream*<br/>
Un puntero a un flujo que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
La dirección de un puntero que recibirá el `IUnknown` del contenedor. Puede ser NULL.

*ppUnkControl*<br/>
enuncia Dirección de un puntero que recibirá el `IUnknown` del control creado. Puede ser NULL.

*iidSink*<br/>
Identificador de interfaz de una interfaz de salida en el objeto contenido.

*punkSink*<br/>
Puntero a la interfaz `IUnknown` del objeto receptor que se va a conectar al punto de conexión especificado por *iidSink* en el objeto contenido después de que el objeto contenido se haya creado correctamente.

*bstrLic*<br/>
BSTR que contiene la licencia para el control.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

`AtlAxCreateControlLicEx` es similar a [AtlAxCreateControlLic](#atlaxcreatecontrollic) , pero también permite recibir un puntero de interfaz al control recién creado y configurar un receptor de eventos para recibir los eventos desencadenados por el control.

### <a name="example"></a>Ejemplo

Vea [hospedar controles ActiveX mediante](../../atl/hosting-activex-controls-using-atl-axhost.md) el método AXHOST de ATL para obtener un ejemplo de cómo utilizar `AtlAxCreateControlLicEx`.

##  <a name="atlaxattachcontrol"></a>AtlAxAttachControl

Asocia un control creado previamente con la ventana especificada.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
de Puntero al `IUnknown` del control.

*hWnd*<br/>
de Identificador de la ventana que va a hospedar el control.

*ppUnkContainer*<br/>
enuncia Un puntero a un puntero al `IUnknown` del objeto contenedor.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Use [AtlAxCreateControlEx](#atlaxcreatecontrolex) y [AtlAxCreateControl](#atlaxcreatecontrol) para crear y adjuntar un control simultáneamente.

> [!NOTE]
>  El objeto de control que se va a adjuntar debe inicializarse correctamente antes de llamar a `AtlAxAttachControl`.

##  <a name="atlaxgethost"></a>AtlAxGetHost

Obtiene un puntero de interfaz directo al contenedor de una ventana especificada (si existe) en función de su identificador.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
de Identificador de la ventana que hospeda el control.

*páginas*<br/>
enuncia `IUnknown` del contenedor del control.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="atlaxgetcontrol"></a>AtlAxGetControl

Obtiene un puntero de interfaz directo al control que se encuentra dentro de una ventana especificada en función de su identificador.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
de Identificador de la ventana que hospeda el control.

*páginas*<br/>
enuncia `IUnknown` del control que se va a hospedar.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="atlsetchildsite"></a>AtlSetChildSite

Llame a esta función para establecer el sitio del objeto secundario en el `IUnknown` del objeto primario.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Parámetros

*punkChild*<br/>
de Puntero a la interfaz `IUnknown` del elemento secundario.

*punkParent*<br/>
de Puntero a la interfaz `IUnknown` del elemento primario.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="atlaxwininit"></a>AtlAxWinInit

Esta función inicializa el código de hospedaje de controles de ATL registrando las clases de ventana **"AtlAxWin80"** y **"AtlAxWinLic80"** más un par de mensajes de ventana personalizados.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización del código de hospedaje del control se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Se debe llamar a esta función antes de usar la API de hospedaje de controles ATL. Después de una llamada a esta función, se puede usar la clase de ventana **"AtlAxWin"** en las llamadas a [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) o [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw), como se describe en el Windows SDK.

##  <a name="atlaxwinterm"></a>AtlAxWinTerm

Esta función anula la inicialización del código de hospedaje de controles de ATL al anular el registro de las clases de ventana **"AtlAxWin80"** y **"AtlAxWinLic80"** .

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Esta función simplemente llama a [UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) como se describe en el Windows SDK.

Llame a esta función para realizar la limpieza después de que todas las ventanas de host existentes se hayan destruido si llamó a [AtlAxWinInit](#atlaxwininit) y ya no necesita crear ventanas de host. Si no llama a esta función, se anulará el registro de la clase de ventana automáticamente cuando finalice el proceso.

##  <a name="atlgetobjectsourceinterface"></a>AtlGetObjectSourceInterface

Llame a esta función para recuperar información sobre la interfaz de origen predeterminada de un objeto.

```
ATLAPI AtlGetObjectSourceInterface(
    IUnknown* punkObj,
    GUID* plibid,
    IID* piid,
    unsigned short* pdwMajor,
    unsigned short* pdwMinor);
```

### <a name="parameters"></a>Parámetros

*punkObj*<br/>
de Puntero al objeto para el que se va a devolver información.

*plibid*<br/>
enuncia Puntero al LIBId de la biblioteca de tipos que contiene la definición de la interfaz de origen.

*piid*<br/>
enuncia Puntero al identificador de interfaz de la interfaz de origen predeterminada del objeto.

*pdwMajor*<br/>
enuncia Puntero al número de versión principal de la biblioteca de tipos que contiene la definición de la interfaz de origen.

*pdwMinor*<br/>
enuncia Puntero al número de versión secundaria de la biblioteca de tipos que contiene la definición de la interfaz de origen.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

`AtlGetObjectSourceInterface` puede proporcionarle el identificador de interfaz de la interfaz de origen predeterminada, junto con el LIBId y los números de versión principal y secundaria de la biblioteca de tipos que describe esa interfaz.

> [!NOTE]
>  Para que esta función recupere correctamente la información solicitada, el objeto representado por *punkObj* debe implementar `IDispatch` (y devolver información de tipo a través de `IDispatch::GetTypeInfo`) y también debe implementar `IProvideClassInfo2` o `IPersist`. La información de tipo de la interfaz de origen debe estar en la misma biblioteca de tipos que la información de tipo de `IDispatch`.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo puede definir una clase de receptor de eventos, `CEasySink`, que reduce el número de argumentos de plantilla que puede pasar a `IDispEventImpl` a los elementos esenciales. `EasyAdvise` y `EasyUnadvise` utilizan `AtlGetObjectSourceInterface` para inicializar los miembros de [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) antes de llamar a [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) o [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Consulte también

[Funciones](../../atl/reference/atl-functions.md)<br/>
[Macros de control compuesto](../../atl/reference/composite-control-macros.md)
