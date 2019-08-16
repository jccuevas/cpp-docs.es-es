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
ms.openlocfilehash: bc39a5deeb270b0426a4b199fc9ba01917c292bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496812"
---
# <a name="cdialogimpl-class"></a>CDialogImpl (clase)

Esta clase proporciona métodos para crear un cuadro de diálogo modal o no modal.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `CDialogImpl`.

*TBase*<br/>
La clase base de la nueva clase. La clase base predeterminada es [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[A](#create)|Crea un cuadro de diálogo no modal.|
|[DestroyWindow](#destroywindow)|Destruye un cuadro de diálogo no modal.|
|[DoModal](#domodal)|Crea un cuadro de diálogo modal.|
|[EndDialog](#enddialog)|Destruye un cuadro de diálogo modal.|

### <a name="cdialogimplbaset-methods"></a>Métodos CDialogImplBaseT

|||
|-|-|
|[GetDialogProc](#getdialogproc)|Devuelve el procedimiento de cuadro de diálogo actual.|
|[MapDialogRect](#mapdialogrect)|Asigna las unidades de cuadro de diálogo del rectángulo especificado a unidades de pantalla (píxeles).|
|[OnFinalMessage](#onfinalmessage)|Se llama después de recibir el último mensaje, normalmente WM_NCDESTROY.|

### <a name="static-functions"></a>Funciones estáticas

|||
|-|-|
|[DialogProc](#dialogproc)|Procesa los mensajes enviados al cuadro de diálogo.|
|[StartDialogProc](#startdialogproc)|Se le llama cuando se recibe el primer mensaje para procesar los mensajes enviados al cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Con `CDialogImpl` puede crear un cuadro de diálogo modal o no modal. `CDialogImpl`proporciona el procedimiento de cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para dirigir los mensajes a los controladores adecuados.

El destructor `~CWindowImplRoot` de clase base garantiza que la ventana ha desaparecido antes de destruir el objeto.

`CDialogImpl` se deriva de `CDialogImplBaseT` que, a su vez, se deriva de `CWindowImplRoot`.

> [!NOTE]
>  La clase debe definir un `IDD` miembro que especifique el identificador de recurso de la plantilla de cuadro de diálogo. Por ejemplo, el Asistente para proyectos ATL agrega automáticamente la siguiente línea a la clase:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

donde `MyDlg` es el **nombre corto** escrito en la página **nombres** del asistente.

|Para obtener más información sobre|Vea|
|--------------------------------|---------|
|Crear controles|[Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md)|
|Usar cuadros de diálogo en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|
|Asistente para proyectos ATL|[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|
|Cuadros de diálogo|[Cuadros de diálogo](/windows/win32/dlgbox/dialog-boxes) y temas posteriores en el Windows SDK|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

##  <a name="create"></a>  CDialogImpl::Create

Crea un cuadro de diálogo no modal.

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
de Identificador de la ventana propietaria.

**& Rect** *rectángulo* de Estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que especifica el tamaño y la posición del cuadro de diálogo.

*dwInitParam*<br/>
de Especifica el valor que se va a pasar al cuadro de diálogo en el parámetro *lParam* del mensaje WM_INITDIALOG.

### <a name="return-value"></a>Valor devuelto

Identificador del cuadro de diálogo que se acaba de crear.

### <a name="remarks"></a>Comentarios

Este cuadro de diálogo se adjunta automáticamente al `CDialogImpl` objeto. Para crear un cuadro de diálogo modal, llame a [DoModal](#domodal). La segunda invalidación anterior solo se usa con [CComControl](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>  CDialogImpl::DestroyWindow

Destruye un cuadro de diálogo no modal.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el cuadro de diálogo se ha destruido correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Devuelve TRUE si el cuadro de diálogo se ha destruido correctamente; en caso contrario, FALSE.

##  <a name="dialogproc"></a>  CDialogImpl::DialogProc

Esta función estática implementa el procedimiento de cuadro de diálogo.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
de Identificador del cuadro de diálogo.

*uMsg*<br/>
de Mensaje enviado al cuadro de diálogo.

*wParam*<br/>
de Información adicional específica del mensaje.

*lParam*<br/>
de Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

TRUE si se procesa el mensaje; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

`DialogProc`usa el mapa de mensajes predeterminado para dirigir los mensajes a los controladores adecuados.

Puede invalidar `DialogProc` para proporcionar un mecanismo diferente para controlar los mensajes.

##  <a name="domodal"></a>  CDialogImpl::DoModal

Crea un cuadro de diálogo modal.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
de Identificador de la ventana propietaria. El valor predeterminado es el valor devuelto de la función [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) de Win32.

*dwInitParam*<br/>
de Especifica el valor que se va a pasar al cuadro de diálogo en el parámetro *lParam* del mensaje WM_INITDIALOG.

### <a name="return-value"></a>Valor devuelto

Si es correcto, el valor del parámetro *nRetCode* especificado en la llamada a [EndDialog](#enddialog). De lo contrario,-1.

### <a name="remarks"></a>Comentarios

Este cuadro de diálogo se adjunta automáticamente al `CDialogImpl` objeto.

Para crear un cuadro de diálogo no modal, llame a [Create](#create).

##  <a name="enddialog"></a>  CDialogImpl::EndDialog

Destruye un cuadro de diálogo modal.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parámetros

*nRetCode*<br/>
de Valor que va a ser devuelto por [CDialogImpl::D omodal](#domodal).

### <a name="return-value"></a>Valor devuelto

TRUE si el cuadro de diálogo está destruido; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

`EndDialog`se debe llamar a mediante el procedimiento de cuadro de diálogo. Una vez destruido el cuadro de diálogo, Windows usa el valor de *nRetCode* como valor devuelto `DoModal`para, que creó el cuadro de diálogo.

> [!NOTE]
>  No llame `EndDialog` a para destruir un cuadro de diálogo no modal. Llame a [CWindow::D estroywindow](../../atl/reference/cwindow-class.md#destroywindow) en su lugar.

##  <a name="getdialogproc"></a>  CDialogImpl::GetDialogProc

Devuelve `DialogProc`, el procedimiento de cuadro de diálogo actual.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Valor devuelto

El procedimiento de cuadro de diálogo actual.

### <a name="remarks"></a>Comentarios

Invalide este método para reemplazar el procedimiento de cuadro de diálogo por el suyo propio.

##  <a name="mapdialogrect"></a>  CDialogImpl::MapDialogRect

Convierte (asigna) las unidades de cuadro de diálogo del rectángulo especificado en unidades de pantalla (píxeles).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una `CRect` estructura Object o [Rect](/windows/win32/api/windef/ns-windef-rect) que va a recibir las coordenadas de cliente de la actualización que incluye la región de actualización.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la actualización se realiza correctamente; 0 si se produce un error en la actualización. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

### <a name="remarks"></a>Comentarios

La función reemplaza las coordenadas de la estructura `RECT` especificada por las coordenadas convertidas, lo que permite utilizar la estructura para crear un cuadro de diálogo o colocar un control dentro de un cuadro de diálogo.

##  <a name="onfinalmessage"></a>  CDialogImpl::OnFinalMessage

Se llama después de recibir el último mensaje `WM_NCDESTROY`(normalmente).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
de Identificador de la ventana que se va a destruir.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que si desea eliminar automáticamente el objeto en el momento de la destrucción de la ventana, puede llamar a **eliminar esto;** aquí.

##  <a name="startdialogproc"></a>  CDialogImpl::StartDialogProc

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
de Identificador del cuadro de diálogo.

*uMsg*<br/>
de Mensaje enviado al cuadro de diálogo.

*wParam*<br/>
de Información adicional específica del mensaje.

*lParam*<br/>
de Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

El procedimiento de ventana.

### <a name="remarks"></a>Comentarios

Después de la llamada inicial `StartDialogProc`a `DialogProc` , se establece como un procedimiento de cuadro de diálogo y las llamadas posteriores van ahí.

## <a name="see-also"></a>Vea también

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
