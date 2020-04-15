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
ms.openlocfilehash: 99ecd4cf04b3eb696f897d6ef5a5e3839d46ef17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331610"
---
# <a name="composite-control-global-functions"></a>Funciones globales de control compuesto

Estas funciones proporcionan compatibilidad para crear cuadros de diálogo y para crear, hospedar y conceder licencias a controles ActiveX.

> [!IMPORTANT]
> Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|Crea un cuadro de diálogo modal a partir de una plantilla de cuadros de diálogo proporcionada por el usuario. El cuadro de diálogo resultante puede contener controles ActiveX.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Crea un cuadro de diálogo no modal a partir de una plantilla de cuadros de diálogo proporcionada por el usuario. El cuadro de diálogo resultante puede contener controles ActiveX.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Crea un control ActiveX, lo inicializa, lo hospeda en la ventana especificada y recupera un puntero de interfaz (o punteros) del control.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Crea un control ActiveX con licencia, lo inicializa, lo hospeda en la ventana especificada y recupera un puntero de interfaz (o punteros) del control.|
|[AtlAxAttachControl](#atlaxattachcontrol)|Asocia un control creado previamente con la ventana especificada.|
|[AtlAxGetHost](#atlaxgethost)|Se utiliza para obtener un puntero de interfaz directa al contenedor para una ventana especificada (si existe), dado su identificador.|
|[AtlAxGetControl](#atlaxgetcontrol)|Se utiliza para obtener un puntero de interfaz directa al control contenido dentro de una ventana especificada (si existe), dado su identificador.|
|[AtlSetChildSite](#atlsetchildsite)|Inicializa el `IUnknown` sitio secundario.|
|[AtlAxWinInit](#atlaxwininit)|Inicializa el código de hospedaje para los objetos AxWin.|
|[AtlAxWinTerm](#atlaxwinterm)|Uninitializes el código de hospedaje para AxWin objetos.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Devuelve información sobre la interfaz de origen predeterminada de un objeto.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlhost.h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a>AtlAxDialogBox

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
[en] Identifica una instancia del módulo cuyo archivo ejecutable contiene la plantilla de cuadro de diálogo.

*lpTemplateName*<br/>
[en] Identifica la plantilla del cuadro de diálogo. Este parámetro es el puntero a una cadena de caracteres terminada en null que especifica el nombre de la plantilla de cuadro de diálogo o un valor entero que especifica el identificador de recurso de la plantilla de cuadro de diálogo. Si el parámetro especifica un identificador de recurso, su palabra de orden superior debe ser cero y su palabra de orden bajo debe contener el identificador. Puede utilizar la macro [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) para crear este valor.

*hWndParent*<br/>
[en] Identifica la ventana que posee el cuadro de diálogo.

*lpDialogProc*<br/>
[en] Apunta al procedimiento del cuadro de diálogo. Para obtener más información sobre el procedimiento del cuadro de diálogo, vea [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
[en] Especifica el valor que se va a pasar al cuadro de diálogo en el parámetro *lParam* del mensaje WM_INITDIALOG.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Para `AtlAxDialogBox` usar con una plantilla de cuadro de diálogo que contiene un control ActiveX, especifique un CLSID, APPID o cadena URL válido como campo de *texto* de la sección **CONTROL** del recurso de cuadro de diálogo, junto con "AtlAxWin80" como campo de nombre de *clase* en la misma sección. A continuación se muestra el aspecto que podría tener una sección **CONTROL** válida:

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

Para obtener más información sobre la edición de scripts de recursos, consulte [Cómo: abrir un archivo](../../windows/how-to-open-a-resource-script-file-in-text-format.md)de script de recursos en formato de texto . Para obtener más información sobre las instrucciones de definición de recursos de control, vea [Parámetros](/windows/win32/menurc/common-control-parameters) de control comunes en Windows SDK: Herramientas de SDK.

Para obtener más información sobre los cuadros de diálogo en general, consulte [DialogBox](/windows/win32/api/winuser/nf-winuser-dialogboxw) y [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) en el Windows SDK.

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a>AtlAxCreateDialog

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
[en] Identifica una instancia del módulo cuyo archivo ejecutable contiene la plantilla de cuadro de diálogo.

*lpTemplateName*<br/>
[en] Identifica la plantilla del cuadro de diálogo. Este parámetro es el puntero a una cadena de caracteres terminada en null que especifica el nombre de la plantilla de cuadro de diálogo o un valor entero que especifica el identificador de recurso de la plantilla de cuadro de diálogo. Si el parámetro especifica un identificador de recurso, su palabra de orden superior debe ser cero y su palabra de orden bajo debe contener el identificador. Puede utilizar la macro [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) para crear este valor.

*hWndParent*<br/>
[en] Identifica la ventana que posee el cuadro de diálogo.

*lpDialogProc*<br/>
[en] Apunta al procedimiento del cuadro de diálogo. Para obtener más información sobre el procedimiento del cuadro de diálogo, vea [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
[en] Especifica el valor que se va a pasar al cuadro de diálogo en el parámetro *lParam* del mensaje WM_INITDIALOG.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

El cuadro de diálogo resultante puede contener controles ActiveX.

Consulte [CreateDialog](/windows/win32/api/winuser/nf-winuser-createdialogw) y [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) en el Windows SDK.

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a>AtlAxCreateControl

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
Puntero a una cadena que se pasará al control. Debe estar formateado de una de las siguientes maneras:

- Un ProgID como`"MSCAL.Calendar.7"`

- Un CLSID como`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una URL como`"<https://www.microsoft.com>"`

- Una referencia a un documento activo como`"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`debe preceder al fragmento HTML para que se designe como una secuencia MSHTML.

*hWnd*<br/>
[en] Controle la ventana a la que se adjuntará el control.

*pStream*<br/>
[en] Puntero a una secuencia que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
[fuera] La dirección de un puntero `IUnknown` que recibirá el contenedor. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta función global proporciona el mismo resultado que llamar a [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *hWnd*, *pStream*, NULL, NULL, NULL, NULL);.

Para crear un control ActiveX con licencia, vea [AtlAxCreateControlLic](#atlaxcreatecontrollic).

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a>AtlAxCreateControlEx

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
Puntero a una cadena que se pasará al control. Debe estar formateado de una de las siguientes maneras:

- Un ProgID como`"MSCAL.Calendar.7"`

- Un CLSID como`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una URL como`"<https://www.microsoft.com>"`

- Una referencia a un documento activo como`"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`debe preceder al fragmento HTML para que se designe como una secuencia MSHTML.

*hWnd*<br/>
[en] Controle la ventana a la que se adjuntará el control.

*pStream*<br/>
[en] Puntero a una secuencia que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
[fuera] La dirección de un puntero `IUnknown` que recibirá el contenedor. Puede ser NULL.

*ppUnkControl*<br/>
[fuera] La dirección de un puntero `IUnknown` que recibirá el del control creado. Puede ser NULL.

*iidSink*<br/>
Identificador de interfaz de una interfaz saliente en el objeto contenido.

*punkSink*<br/>
Puntero a `IUnknown` la interfaz del objeto receptor que se va a conectar al punto de conexión especificado por *iidSink* en el objeto contenido después de que el objeto contenido se haya creado correctamente.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

`AtlAxCreateControlEx`es similar a [AtlAxCreateControl,](#atlaxcreatecontrol) pero también le permite recibir un puntero de interfaz al control recién creado y configurar un receptor de eventos para recibir eventos desencadenados por el control.

Para crear un control ActiveX con licencia, vea [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a>AtlAxCreateControlLic

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
Puntero a una cadena que se pasará al control. Debe estar formateado de una de las siguientes maneras:

- Un ProgID como`"MSCAL.Calendar.7"`

- Un CLSID como`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una URL como`"<https://www.microsoft.com>"`

- Una referencia a un documento activo como`"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`debe preceder al fragmento HTML para que se designe como una secuencia MSHTML.

*hWnd*<br/>
Controle la ventana a la que se adjuntará el control.

*pStream*<br/>
Puntero a una secuencia que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
La dirección de un puntero `IUnknown` que recibirá el contenedor. Puede ser NULL.

*bstrLic*<br/>
El BSTR que contiene la licencia para el control.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="example"></a>Ejemplo

Consulte [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) `AtlAxCreateControlLic`para obtener un ejemplo de cómo usar .

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a>AtlAxCreateControlLicEx

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
Puntero a una cadena que se pasará al control. Debe estar formateado de una de las siguientes maneras:

- Un ProgID como`"MSCAL.Calendar.7"`

- Un CLSID como`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una URL como`"<https://www.microsoft.com>"`

- Una referencia a un documento activo como`"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`debe preceder al fragmento HTML para que se designe como una secuencia MSHTML.

*hWnd*<br/>
Controle la ventana a la que se adjuntará el control.

*pStream*<br/>
Puntero a una secuencia que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
La dirección de un puntero `IUnknown` que recibirá el contenedor. Puede ser NULL.

*ppUnkControl*<br/>
[fuera] La dirección de un puntero `IUnknown` que recibirá el del control creado. Puede ser NULL.

*iidSink*<br/>
Identificador de interfaz de una interfaz saliente en el objeto contenido.

*punkSink*<br/>
Puntero a `IUnknown` la interfaz del objeto receptor que se va a conectar al punto de conexión especificado por *iidSink* en el objeto contenido después de que el objeto contenido se haya creado correctamente.

*bstrLic*<br/>
El BSTR que contiene la licencia para el control.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

`AtlAxCreateControlLicEx`es similar a [AtlAxCreateControlLic,](#atlaxcreatecontrollic) pero también le permite recibir un puntero de interfaz al control recién creado y configurar un receptor de eventos para recibir eventos desencadenados por el control.

### <a name="example"></a>Ejemplo

Consulte [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) `AtlAxCreateControlLicEx`para obtener un ejemplo de cómo usar .

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a>AtlAxAttachControl

Asocia un control creado previamente con la ventana especificada.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
[en] Un puntero `IUnknown` a la del control.

*hWnd*<br/>
[en] Controlar a la ventana que hospedará el control.

*ppUnkContainer*<br/>
[fuera] Un puntero a un `IUnknown` puntero al del objeto contenedor.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Utilice [AtlAxCreateControlEx](#atlaxcreatecontrolex) y [AtlAxCreateControl](#atlaxcreatecontrol) para crear y adjuntar simultáneamente un control.

> [!NOTE]
> El objeto de control que se `AtlAxAttachControl`va a adjuntar debe inicializarse correctamente antes de llamar a .

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a>AtlAxGetHost

Obtiene un puntero de interfaz directo al contenedor de una ventana especificada (si existe) en función de su identificador.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
[en] Identificador de la ventana que hospeda el control.

*Pp*<br/>
[fuera] El `IUnknown` del contenedor del control.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a>AtlAxGetControl

Obtiene un puntero de interfaz directo al control que se encuentra dentro de una ventana especificada en función de su identificador.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
[en] Identificador de la ventana que hospeda el control.

*Pp*<br/>
[fuera] El `IUnknown` del control que se hospeda.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a>AtlSetChildSite

Llame a esta función para establecer `IUnknown` el sitio del objeto secundario en el del objeto primario.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Parámetros

*punkChild*<br/>
[en] Un puntero `IUnknown` a la interfaz del elemento secundario.

*punkParent*<br/>
[en] Un puntero `IUnknown` a la interfaz del elemento primario.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a>AtlAxWinInit

Esta función inicializa el código de hospedaje de control de ATL mediante el registro de las clases de ventana **"AtlAxWin80"** y **"AtlAxWinLic80"** además de un par de mensajes de ventana personalizados.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización del código de hospedaje de control se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Se debe llamar a esta función antes de usar la API de hospedaje de control ATL. Después de una llamada a esta función, la clase de ventana **"AtlAxWin"** se puede usar en llamadas a [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) o [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw), como se describe en el Windows SDK.

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a>AtlAxWinTerm

Esta función anula la inicialización del código de hospedaje de control de ATL anula el registro de las clases de ventana **"AtlAxWin80"** y **"AtlAxWinLic80".**

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Esta función simplemente llama a [UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) como se describe en el Windows SDK.

Llame a esta función para limpiar después de que se hayan destruido todas las ventanas de host existentes si llamó a [AtlAxWinInit](#atlaxwininit) y ya no es necesario crear ventanas de host. Si no llama a esta función, la clase window se anulará el registro automáticamente cuando finalice el proceso.

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a>AtlGetObjectSourceInterface

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
[en] Puntero al objeto para el que se va a devolver información.

*plibid*<br/>
[fuera] Puntero al LIBID de la biblioteca de tipos que contiene la definición de la interfaz de origen.

*piid*<br/>
[fuera] Un puntero al identificador de interfaz de la interfaz de origen predeterminada del objeto.

*pdwMajor*<br/>
[fuera] Puntero al número de versión principal de la biblioteca de tipos que contiene la definición de la interfaz de origen.

*pdwMinor*<br/>
[fuera] Puntero al número de versión secundaria de la biblioteca de tipos que contiene la definición de la interfaz de origen.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

`AtlGetObjectSourceInterface`puede proporcionarle el ID de interfaz de la interfaz de origen predeterminada, junto con el LIBID y los números de versión principal y secundaria de la biblioteca de tipos que describe esa interfaz.

> [!NOTE]
> Para que esta función recupere correctamente la información solicitada, `IDispatch` el objeto representado `IDispatch::GetTypeInfo`por *punkObj* debe `IProvideClassInfo2` `IPersist`implementar (y devolver información de tipo a través de ) además de que también debe implementar o . La información de tipo para la interfaz de origen `IDispatch`debe estar en la misma biblioteca de tipos que la información de tipo para .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo `CEasySink`puede definir una clase de receptor de `IDispEventImpl` eventos, que reduce el número de argumentos de plantilla que puede pasar a los elementos esenciales desnudos. `EasyAdvise`y `EasyUnadvise` `AtlGetObjectSourceInterface` se usa para inicializar los miembros [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) antes de llamar a [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) o [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)<br/>
[Macros de control compuesto](../../atl/reference/composite-control-macros.md)
