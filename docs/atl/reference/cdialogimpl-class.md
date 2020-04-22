---
title: CDialogImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
ms.openlocfilehash: d5ab7293f73429a93c3fcab243c2e34d3c78f28a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747705"
---
# <a name="cdialogimpl-class"></a>CDialogImpl (clase)

Esta clase proporciona métodos para crear un cuadro de diálogo modal o no modal.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `CDialogImpl`de .

*TBase*<br/>
La clase base de tu nueva clase. La clase base predeterminada es [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Crear](#create)|Crea un cuadro de diálogo no quede indecitado.|
|[DestroyWindow](#destroywindow)|Destruye un cuadro de diálogo no codificador.|
|[DoModal](#domodal)|Crea un cuadro de diálogo modal.|
|[EndDialog](#enddialog)|Destruye un cuadro de diálogo modal.|

### <a name="cdialogimplbaset-methods"></a>Métodos CDialogImplBaseT

|||
|-|-|
|[GetDialogProc](#getdialogproc)|Devuelve el procedimiento del cuadro de diálogo actual.|
|[MapDialogRect](#mapdialogrect)|Asigna las unidades de cuadro de diálogo del rectángulo especificado a unidades de pantalla (píxeles).|
|[OnFinalMessage](#onfinalmessage)|Se llama después de recibir el último mensaje, normalmente WM_NCDESTROY.|

### <a name="static-functions"></a>Funciones estáticas

|||
|-|-|
|[DialogProc](#dialogproc)|Procesa los mensajes enviados al cuadro de diálogo.|
|[StartDialogProc](#startdialogproc)|Se llama cuando se recibe el primer mensaje para procesar los mensajes enviados al cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

Con `CDialogImpl` usted puede crear un cuadro de diálogo modal o no modal. `CDialogImpl`proporciona el procedimiento de cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para dirigir los mensajes a los controladores adecuados.

El destructor `~CWindowImplRoot` de clase base garantiza que la ventana se ha ido antes de destruir el objeto.

`CDialogImpl` se deriva de `CDialogImplBaseT` que, a su vez, se deriva de `CWindowImplRoot`.

> [!NOTE]
> La clase debe `IDD` definir un miembro que especifique el identificador de recurso de plantilla de cuadro de diálogo. Por ejemplo, el Asistente para proyectos ATL agrega automáticamente la siguiente línea a la clase:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

donde `MyDlg` se encuentra el **nombre corto** introducido en la página **Nombres** del asistente.

|Para más información sobre|Vea|
|--------------------------------|---------|
|Crear controles|[Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md)|
|Uso de cuadros de diálogo en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|
|Asistente para proyectos ATL|[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|
|Cuadros de diálogo|[Cuadros de diálogo](/windows/win32/dlgbox/dialog-boxes) y temas posteriores en el Windows SDK|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="cdialogimplcreate"></a><a name="create"></a>CDialogImpl::Crear

Crea un cuadro de diálogo no quede indecitado.

```
HWND Create(
    HWND hWndParent,
    LPARAM dwInitParam = NULL );

HWND Create(
    HWND hWndParent,
    RECT&,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
[en] El identificador de la ventana del propietario.

**RECT&** *rect* [in] Una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que especifique el tamaño y la posición del cuadro de diálogo.

*dwInitParam*<br/>
[en] Especifica el valor que se va a pasar al cuadro de diálogo en el parámetro *lParam* del mensaje WM_INITDIALOG.

### <a name="return-value"></a>Valor devuelto

El identificador del cuadro de diálogo recién creado.

### <a name="remarks"></a>Observaciones

Este cuadro de diálogo `CDialogImpl` se adjunta automáticamente al objeto. Para crear un cuadro de diálogo modal, llame a [DoModal](#domodal). La segunda invalidación anterior solo se utiliza con [CComControl](../../atl/reference/ccomcontrol-class.md).

## <a name="cdialogimpldestroywindow"></a><a name="destroywindow"></a>CDialogImpl::DestroyWindow

Destruye un cuadro de diálogo no codificador.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Valor devuelto

TRUESi el cuadro de diálogo se destruyó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Devuelve TRUE si el cuadro de diálogo se destruyó correctamente; de lo contrario FALSO.

## <a name="cdialogimpldialogproc"></a><a name="dialogproc"></a>CDialogImpl::DialogProc

Esta función estática implementa el procedimiento del cuadro de diálogo.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
[en] El identificador del cuadro de diálogo.

*uMsg*<br/>
[en] El mensaje enviado al cuadro de diálogo.

*wParam*<br/>
[en] Información adicional específica del mensaje.

*lParam*<br/>
[en] Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

TRUESi se procesa el mensaje; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

`DialogProc`utiliza el mapa de mensajes predeterminado para dirigir los mensajes a los controladores adecuados.

Puede invalidar `DialogProc` para proporcionar un mecanismo diferente para controlar los mensajes.

## <a name="cdialogimpldomodal"></a><a name="domodal"></a>CDialogImpl::DoModal

Crea un cuadro de diálogo modal.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
[en] El identificador de la ventana del propietario. El valor predeterminado es el valor devuelto de la función [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32.

*dwInitParam*<br/>
[en] Especifica el valor que se va a pasar al cuadro de diálogo en el parámetro *lParam* del mensaje WM_INITDIALOG.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el valor del parámetro *nRetCode* especificado en la llamada a [EndDialog](#enddialog). En caso contrario, -1.

### <a name="remarks"></a>Observaciones

Este cuadro de diálogo `CDialogImpl` se adjunta automáticamente al objeto.

Para crear un cuadro de diálogo no distingueso, llame a [Crear](#create).

## <a name="cdialogimplenddialog"></a><a name="enddialog"></a>CDialogImpl::EndDialog

Destruye un cuadro de diálogo modal.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parámetros

*nRetCode*<br/>
[en] Valor que va a devolver [CDialogImpl::DoModal](#domodal).

### <a name="return-value"></a>Valor devuelto

TRUESi se destruye el cuadro de diálogo; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

`EndDialog`debe llamarse a través del procedimiento de diálogo. Después de destruir el cuadro de diálogo, Windows utiliza el `DoModal`valor de *nRetCode* como valor devuelto para , que creó el cuadro de diálogo.

> [!NOTE]
> No llame `EndDialog` para destruir un cuadro de diálogo no codificador. Llame a [CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) en su lugar.

## <a name="cdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CDialogImpl::GetDialogProc

Devuelve `DialogProc`, el procedimiento del cuadro de diálogo actual.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Valor devuelto

El procedimiento del cuadro de diálogo actual.

### <a name="remarks"></a>Observaciones

Invalide este método para reemplazar el procedimiento de diálogo por el suyo propio.

## <a name="cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a>CDialogImpl::MapDialogRect

Convierte (asigna) las unidades de cuadro de diálogo del rectángulo especificado en unidades de pantalla (píxeles).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a `CRect` un objeto o estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que va a recibir las coordenadas de cliente de la actualización que encierra la región de actualización.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la actualización se realiza correctamente; 0 si se produce un error en la actualización. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

### <a name="remarks"></a>Observaciones

La función reemplaza las coordenadas `RECT` de la estructura especificada por las coordenadas convertidas, lo que permite utilizar la estructura para crear un cuadro de diálogo o colocar un control dentro de un cuadro de diálogo.

## <a name="cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a>CDialogImpl::OnFinalMessage

Se llama después de `WM_NCDESTROY`recibir el último mensaje (normalmente ).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
[en] Un mango a la ventana que se está destruyendo.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que si desea eliminar automáticamente el objeto tras la destrucción de la ventana, puede llamar a **delete this;** aquí.

## <a name="cdialogimplstartdialogproc"></a><a name="startdialogproc"></a>CDialogImpl::StartDialogProc

Se llama solo una vez, cuando se recibe el primer mensaje, para procesar los mensajes enviados al cuadro de diálogo.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
[en] El identificador del cuadro de diálogo.

*uMsg*<br/>
[en] El mensaje enviado al cuadro de diálogo.

*wParam*<br/>
[en] Información adicional específica del mensaje.

*lParam*<br/>
[en] Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

El procedimiento de ventana.

### <a name="remarks"></a>Observaciones

Después de `StartDialogProc`la `DialogProc` llamada inicial a , se establece como un procedimiento de diálogo, y otras llamadas van allí.

## <a name="see-also"></a>Vea también

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
