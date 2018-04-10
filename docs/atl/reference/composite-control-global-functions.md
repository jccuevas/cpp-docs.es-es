---
title: Funciones globales de Control compuesto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d5a062ea9477df9db026c75bc775df804ed86da4
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="composite-control-global-functions"></a>Funciones globales de controles compuestos
Estas funciones proporcionan compatibilidad para crear cuadros de diálogo y para crear, hospedar y otorgar licencias a controles ActiveX.  
  
> [!IMPORTANT]
>  Las funciones se enumeran en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
|||  
|-|-|  
|[AtlAxDialogBox](#atlaxdialogbox)|Crea un cuadro de diálogo modal a partir de una plantilla de cuadros de diálogo proporcionada por el usuario. El cuadro de diálogo resultante puede contener controles ActiveX.|  
|[AtlAxCreateDialog](#atlaxcreatedialog)|Crea un cuadro de diálogo no modal a partir de una plantilla de cuadros de diálogo proporcionada por el usuario. El cuadro de diálogo resultante puede contener controles ActiveX.|  
|[AtlAxCreateControl](#atlaxcreatecontrol)|Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada.|  
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Crea un control ActiveX, lo inicializa, lo hospeda en la ventana especificada y recupera un puntero de interfaz (o punteros) del control.|  
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada.|  
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Crea un control ActiveX con licencia, lo inicializa, lo hospeda en la ventana especificada y recupera un puntero de interfaz (o punteros) del control.|  
|[AtlAxAttachControl](#atlaxattachcontrol)|Asocia un control creado previamente con la ventana especificada.|  
|[AtlAxGetHost](#atlaxgethost)|Utilizado para obtener un puntero de interfaz directo al contenedor de una ventana especificada (si existe), función de su identificador.|  
|[AtlAxGetControl](#atlaxgetcontrol)|Usar para obtener un puntero de interfaz directo al control que se encuentra dentro de una ventana especificada (si existe), función de su identificador.|  
|[AtlSetChildSite](#atlsetchildsite)|Inicializa el **IUnknown** del sitio secundario.|  
|[AtlAxWinInit](#atlaxwininit)|Inicializa el código de hospedaje para los objetos de AxWin.|  
|[AtlAxWinTerm](#atlaxwinterm)|Desinicializa el código de hospedaje para los objetos de AxWin.|  
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Devuelve información acerca de la interfaz de origen predeterminada de un objeto.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlhost.h  

##  <a name="atlaxdialogbox"></a>  AtlAxDialogBox  
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
 `hInstance`  
 [in] Identifica una instancia del módulo cuyo archivo ejecutable contiene la plantilla de cuadro de diálogo.  
  
 `lpTemplateName`  
 [in] Identifica la plantilla de cuadro de diálogo. Este parámetro es el puntero a una cadena de caracteres terminada en null que especifica el nombre de la plantilla de cuadro de diálogo o un valor entero que especifica el identificador de recursos de la plantilla de cuadro de diálogo. Si el parámetro especifica un identificador de recursos, la palabra de orden superior debe ser cero y la palabra de orden inferior debe contener el identificador. Puede usar el [MAKEINTRESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms648029) macro para crear este valor.  
  
 `hWndParent`  
 [in] Identifica la ventana propietaria del cuadro de diálogo.  
  
 `lpDialogProc`  
 [in] Señala al procedimiento de cuadro de diálogo. Para obtener más información sobre el procedimiento de cuadro de diálogo, vea [función DialogProc](http://msdn.microsoft.com/library/windows/desktop/ms645469).  
  
 `dwInitParam`  
 [in] Especifica el valor que debe pasarse al cuadro de diálogo en el **lParam** parámetro de la **WM_INITDIALOG** mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Usar **AtlAxCreateDialog** con una plantilla de cuadro de diálogo que contiene un control ActiveX, especifique una válida **CLSID**, **APPID** o una cadena de dirección URL como el *texto* campo de la **CONTROL** sección del recurso de cuadro de diálogo, junto con "AtlAxWin80" como el *nombre de la clase* campo en la misma sección. El siguiente ejemplo muestra qué válido **CONTROL** sección podría ser similar:  
  
```  
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,  
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100  
```  
  
 Para obtener más información acerca de cómo editar secuencias de comandos de recursos, consulte [Cómo: abrir un archivo de Script de recursos en formato de texto](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Para obtener más información sobre las instrucciones de definición de recursos de control, vea [parámetros comunes de Control](http://msdn.microsoft.com/library/windows/desktop/aa380902) en Windows SDK*: herramientas de SDK*.  
  
 Para obtener más información sobre los cuadros de diálogo en general, consulte [DialogBox](http://msdn.microsoft.com/library/windows/desktop/ms645452) y [CreateDialogParam](http://msdn.microsoft.com/library/windows/desktop/ms645445) en el SDK de Windows.  
  
##  <a name="atlaxcreatedialog"></a>  AtlAxCreateDialog  
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
 `hInstance`  
 [in] Identifica una instancia del módulo cuyo archivo ejecutable contiene la plantilla de cuadro de diálogo.  
  
 `lpTemplateName`  
 [in] Identifica la plantilla de cuadro de diálogo. Este parámetro es el puntero a una cadena de caracteres terminada en null que especifica el nombre de la plantilla de cuadro de diálogo o un valor entero que especifica el identificador de recursos de la plantilla de cuadro de diálogo. Si el parámetro especifica un identificador de recursos, la palabra de orden superior debe ser cero y la palabra de orden inferior debe contener el identificador. Puede usar el [MAKEINTRESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms648029) macro para crear este valor.  
  
 `hWndParent`  
 [in] Identifica la ventana propietaria del cuadro de diálogo.  
  
 `lpDialogProc`  
 [in] Señala al procedimiento de cuadro de diálogo. Para obtener más información sobre el procedimiento de cuadro de diálogo, vea [función DialogProc](http://msdn.microsoft.com/library/windows/desktop/ms645469).  
  
 `dwInitParam`  
 [in] Especifica el valor que debe pasarse al cuadro de diálogo en el **lParam** parámetro de la **WM_INITDIALOG** mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 El cuadro de diálogo resultante puede contener controles ActiveX.  
  
 Vea [CreateDialog](http://msdn.microsoft.com/library/windows/desktop/ms645434) y [CreateDialogParam](http://msdn.microsoft.com/library/windows/desktop/ms645445) en el SDK de Windows.  
  
##  <a name="atlaxcreatecontrol"></a>  AtlAxCreateControl  
 Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada.  
  

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Un puntero a una cadena que se va a pasar al control. Debe tener el formato de una de las maneras siguientes:  
  
-   A ProgID such as "MSCAL.Calendar.7"  
  
-   A CLSID such as "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Una dirección URL como "http://www.microsoft.com"  
  
-   Una referencia a un documento activo como "file://\\\Documents\MyDoc.doc"  
  
-   Un fragmento de HTML, como "MSHTML:\<HTML >\<cuerpo > se trata de una línea de texto\</cuerpo >\</HTML más externas >"  
  
    > [!NOTE]
    >  "MSHTML:" debe preceder el fragmento HTML para que se designa como una secuencia MSHTML.  
  
 `hWnd`  
 [in] Identificador de la ventana que el control se adjuntará a.  
  
 `pStream`  
 [in] Un puntero a una secuencia que se usa para inicializar las propiedades del control. Puede ser **NULL**.  
  
 `ppUnkContainer`  
 [out] La dirección de un puntero que va a recibir el **IUnknown** del contenedor. Puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función global proporciona el mismo resultado que llamar al método [AtlAxCreateControlEx](#atlaxcreatecontrolex)( `lpszName` **,** `hWnd` **,** `pStream` **, NULL, NULL, NULL, NULL** );.  
  
 Para crear un control ActiveX con licencia, consulte [AtlAxCreateControlLic](#atlaxcreatecontrollic).  
  
##  <a name="atlaxcreatecontrolex"></a>  AtlAxCreateControlEx  
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
 `lpszName`  
 Un puntero a una cadena que se va a pasar al control. Debe tener el formato de una de las maneras siguientes:  
  
-   A ProgID such as "MSCAL.Calendar.7"  
  
-   A CLSID such as "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Una dirección URL como "http://www.microsoft.com"  
  
-   Una referencia a un documento activo como "file://\\\Documents\MyDoc.doc"  
  
-   Un fragmento de HTML, como "MSHTML:\<HTML >\<cuerpo > se trata de una línea de texto\</cuerpo >\</HTML más externas >"  
  
    > [!NOTE]
    >  "MSHTML:" debe preceder el fragmento HTML para que se designa como una secuencia MSHTML.  
  
 `hWnd`  
 [in] Identificador de la ventana que el control se adjuntará a.  
  
 `pStream`  
 [in] Un puntero a una secuencia que se usa para inicializar las propiedades del control. Puede ser **NULL**.  
  
 `ppUnkContainer`  
 [out] La dirección de un puntero que va a recibir el **IUnknown** del contenedor. Puede ser **NULL**.  
  
 `ppUnkControl`  
 [out] La dirección de un puntero que va a recibir el **IUnknown** del control creado. Puede ser **NULL**.  
  
 `iidSink`  
 El identificador de la interfaz de una interfaz de salida en el objeto contenido.  
  
 *punkSink*  
 Un puntero a la **IUnknown** interfaz del objeto receptor que se conectará al punto de conexión especificado por `iidSink` en el objeto contenido una vez creado correctamente el objeto contenido.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 `AtlAxCreateControlEx` es similar a [AtlAxCreateControl](#atlaxcreatecontrol) , pero también permite recibir un puntero de interfaz al control recién creado y configurado un receptor de eventos para recibir eventos desencadenados por el control.  
  
 Para crear un control ActiveX con licencia, consulte [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).  
  
##  <a name="atlaxcreatecontrollic"></a>  AtlAxCreateControlLic  
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
 `lpszName`  
 Un puntero a una cadena que se va a pasar al control. Debe tener el formato de una de las maneras siguientes:  
  
-   A ProgID such as "MSCAL.Calendar.7"  
  
-   A CLSID such as "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Una dirección URL como "http://www.microsoft.com"  
  
-   Una referencia a un documento activo como "file://\\\Documents\MyDoc.doc"  
  
-   Un fragmento de HTML, como "MSHTML:\<HTML >\<cuerpo > se trata de una línea de texto\</cuerpo >\</HTML más externas >"  
  
    > [!NOTE]
    >  "MSHTML:" debe preceder el fragmento HTML para que se designa como una secuencia MSHTML.  
  
 `hWnd`  
 Identificador de la ventana que el control se adjuntará a.  
  
 `pStream`  
 Un puntero a una secuencia que se usa para inicializar las propiedades del control. Puede ser **NULL**.  
  
 `ppUnkContainer`  
 La dirección de un puntero que va a recibir el **IUnknown** del contenedor. Puede ser **NULL**.  
  
 `bstrLic`  
 BSTR que contiene la licencia para el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="example"></a>Ejemplo  
 Vea [hospedaje de controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo de cómo usar `AtlAxCreateControlLic`.  
  
##  <a name="atlaxcreatecontrollicex"></a>  AtlAxCreateControlLicEx  
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
 `lpszName`  
 Un puntero a una cadena que se va a pasar al control. Debe tener el formato de una de las maneras siguientes:  
  
-   A ProgID such as "MSCAL.Calendar.7"  
  
-   A CLSID such as "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Una dirección URL como "http://www.microsoft.com"  
  
-   Una referencia a un documento activo como "file://\\\Documents\MyDoc.doc"  
  
-   Un fragmento de HTML, como "MSHTML:\<HTML >\<cuerpo > se trata de una línea de texto\</cuerpo >\</HTML más externas >"  
  
    > [!NOTE]
    >  "MSHTML:" debe preceder el fragmento HTML para que se designa como una secuencia MSHTML.  
  
 `hWnd`  
 Identificador de la ventana que el control se adjuntará a.  
  
 `pStream`  
 Un puntero a una secuencia que se usa para inicializar las propiedades del control. Puede ser **NULL**.  
  
 `ppUnkContainer`  
 La dirección de un puntero que va a recibir el **IUnknown** del contenedor. Puede ser **NULL**.  
  
 `ppUnkControl`  
 [out] La dirección de un puntero que va a recibir el **IUnknown** del control creado. Puede ser **NULL**.  
  
 `iidSink`  
 El identificador de la interfaz de una interfaz de salida en el objeto contenido.  
  
 *punkSink*  
 Un puntero a la **IUnknown** interfaz del objeto receptor que se conectará al punto de conexión especificado por `iidSink` en el objeto contenido una vez creado correctamente el objeto contenido.  
  
 `bstrLic`  
 BSTR que contiene la licencia para el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 `AtlAxCreateControlLicEx` es similar a [AtlAxCreateControlLic](#atlaxcreatecontrollic) , pero también permite recibir un puntero de interfaz al control recién creado y configurado un receptor de eventos para recibir eventos desencadenados por el control.  
  
### <a name="example"></a>Ejemplo  
 Vea [hospedaje de controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo de cómo usar `AtlAxCreateControlLicEx`.  
  
##  <a name="atlaxattachcontrol"></a>  AtlAxAttachControl  
 Asocia un control creado previamente con la ventana especificada.  
  
```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parámetros  
 `pControl`  
 [in] Un puntero a la **IUnknown** del control.  
  
 `hWnd`  
 [in] Identificador de la ventana que se va a hospedar el control.  
  
 `ppUnkContainer`  
 [out] Un puntero a un puntero a la **IUnknown** del objeto contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Use [AtlAxCreateControlEx](#atlaxcreatecontrolex) y [AtlAxCreateControl](#atlaxcreatecontrol) para crear y adjuntar un control simultáneamente.  
  
> [!NOTE]
>  El objeto de control que se va a adjuntar debe inicializarse correctamente antes de llamar a `AtlAxAttachControl`.  
  
##  <a name="atlaxgethost"></a>  AtlAxGetHost  
 Obtiene un puntero de interfaz directo al contenedor de una ventana especificada (si existe) en función de su identificador.  
  
```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 `h`  
 [in] Identificador de la ventana que hospeda el control.  
  
 `pp`  
 [out] El **IUnknown** del contenedor del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl  
 Obtiene un puntero de interfaz directo al control que se encuentra dentro de una ventana especificada en función de su identificador.  
  
```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 `h`  
 [in] Identificador de la ventana que hospeda el control.  
  
 `pp`  
 [out] El **IUnknown** del control hospedado.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="atlsetchildsite"></a>  AtlSetChildSite  
 Llame a esta función para establecer el sitio del objeto secundario en el **IUnknown** del objeto primario.  
  
```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```  
  
### <a name="parameters"></a>Parámetros  
 *punkChild*  
 [in] Un puntero a la **IUnknown** interfaz del elemento secundario.  
  
 `punkParent`  
 [in] Un puntero a la **IUnknown** interfaz del elemento primario.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
##  <a name="atlaxwininit"></a>  AtlAxWinInit  
 Esta función inicializa el código que hospeda al registrar los controles de ATL la **"AtlAxWin80"** y **"AtlAxWinLic80"** clases de ventana junto con un par de mensajes de ventana personalizados.  
  
```
ATLAPI_(BOOL) AtlAxWinInit();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la inicialización del control de código de hospedaje se realizó correctamente; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse antes de usar la API de hospedaje los controles de ATL. Después de una llamada a esta función, el **"AtlAxWin"** clase de ventana se puede utilizar en las llamadas a [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) o [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680), tal y como se describe en el SDK de Windows.  

##  <a name="atlaxwinterm"></a>  AtlAxWinTerm  
 Esta función anula la inicialización controles de ATL anulando el registro código que hospeda el **"AtlAxWin80"** y **"AtlAxWinLic80"** clases de ventana.  
  
```
inline BOOL AtlAxWinTerm();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve **TRUE**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función simplemente llama [UnregisterClass](http://msdn.microsoft.com/library/windows/desktop/ms644899) tal y como se describe en el SDK de Windows.  
  
 Llame a esta función para realizar una limpieza después de que se hayan destruido todas las ventanas de host existente si llama a [AtlAxWinInit](#atlaxwininit) y ya no necesita crear ventanas de host. Si no llama a esta función, la clase de ventana será anular el registro automáticamente cuando finaliza el proceso.  
  
##  <a name="atlgetobjectsourceinterface"></a>  AtlGetObjectSourceInterface  
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
 `punkObj`  
 [in] Un puntero al objeto para el que se devolverá información.  
  
 `plibid`  
 [out] Un puntero a LIBID de la biblioteca de tipos que contiene la definición de la interfaz de origen.  
  
 `piid`  
 [out] Un puntero al identificador de interfaz de la interfaz de origen predeterminada del objeto.  
  
 *pdwMajor*  
 [out] Un puntero al número de versión principal de la biblioteca de tipos que contiene la definición de la interfaz de origen.  
  
 *pdwMinor*  
 [out] Un puntero al número de versión secundaria de la biblioteca de tipos que contiene la definición de la interfaz de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 `AtlGetObjectSourceInterface` puede proporcionar, con el identificador de interfaz de la interfaz de origen predeterminada, junto con LIBID y principales y los números de versión secundaria de la biblioteca de tipos que describen esa interfaz.  
  
> [!NOTE]
>  Para que esta función recuperar correctamente la información solicitada, el objeto representado por `punkObj` debe implementar `IDispatch` (y devolver información de tipo a través de **IDispatch:: GetTypeInfo**) y también debe implementan `IProvideClassInfo2` o `IPersist`. La información de tipo de la interfaz de origen debe estar en la misma biblioteca de tipos como la información de tipo para `IDispatch`.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo se puede definir una clase de receptor de eventos, `CEasySink`, que reduce el número de argumentos de plantilla que puede pasar a `IDispEventImpl` a las funciones esenciales. `EasyAdvise` y `EasyUnadvise` usar `AtlGetObjectSourceInterface` para inicializar el [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) miembros antes de llamar a [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) o [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).  
  
 [!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)   
 [Macros de control compuesto](../../atl/reference/composite-control-macros.md)
