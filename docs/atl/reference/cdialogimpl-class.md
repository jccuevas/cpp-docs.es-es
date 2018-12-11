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
ms.openlocfilehash: b4844ed2246b5e700d9dc1895c3292cdde4efe8b
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178153"
---
# <a name="cdialogimpl-class"></a>CDialogImpl (clase)

Esta clase proporciona métodos para crear un cuadro de diálogo modal o no modal.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `CDialogImpl`.

*TBase*<br/>
La clase base de la nueva clase. La clase base predeterminada es [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Crear](#create)|Crea un cuadro de diálogo no modal.|
|[DestroyWindow](#destroywindow)|Destruye un cuadro de diálogo no modal.|
|[DoModal](#domodal)|Crea un cuadro de diálogo modal.|
|[EndDialog](#enddialog)|Destruye un cuadro de diálogo modal.|

### <a name="cdialogimplbaset-methods"></a>Métodos CDialogImplBaseT

|||
|-|-|
|[GetDialogProc](#getdialogproc)|Devuelve el procedimiento de cuadro de diálogo actual.|
|[MapDialogRect](#mapdialogrect)|Las unidades de cuadro de diálogo del rectángulo especificado se asigna a las unidades de pantalla (píxeles).|
|[OnFinalMessage](#onfinalmessage)|Se llama después de recibir el último mensaje, normalmente WM_NCDESTROY.|

### <a name="static-functions"></a>Funciones estáticas

|||
|-|-|
|[Función DialogProc](#dialogproc)|Procesa los mensajes enviados al cuadro de diálogo.|
|[StartDialogProc](#startdialogproc)|Se llama cuando se recibe el primer mensaje procesar los mensajes enviados al cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Con `CDialogImpl` puede crear un cuadro de diálogo modal o no modal. `CDialogImpl` proporciona el procedimiento de cuadro de diálogo, que usa el mapa de mensajes predeterminado para dirigir mensajes a los controladores adecuados.

El destructor de clase base `~CWindowImplRoot` garantiza que se ha eliminado la ventana antes de destruir el objeto.

`CDialogImpl` se deriva de `CDialogImplBaseT` que, a su vez, se deriva de `CWindowImplRoot`.

> [!NOTE]
>  La clase debe definir un `IDD` miembro que especifica el identificador de recurso de plantilla de cuadro de diálogo. Por ejemplo, el Asistente para proyectos ATL agrega automáticamente la siguiente línea a la clase:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

donde `MyDlg` es el **nombre corto** especificadas en el asistente **nombres** página.

|Para obtener más información sobre|Vea|
|--------------------------------|---------|
|Crear controles|[Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md)|
|Uso de cuadros de diálogo ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|
|Asistente para proyectos ATL|[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|
|Cuadros de diálogo|[Cuadros de diálogo](/windows/desktop/dlgbox/dialog-boxes) y los temas siguientes en el SDK de Windows|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

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
[in] El identificador de la ventana propietaria.

**RECT &** *rect* [in] un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que especifica el cuadro de diálogo tamaño y posición.

*dwInitParam*<br/>
[in] Especifica el valor para pasar al cuadro de diálogo en el *lParam* parámetro del mensaje WM_INITDIALOG.

### <a name="return-value"></a>Valor devuelto

El identificador para el cuadro de diálogo recién creado.

### <a name="remarks"></a>Comentarios

Este cuadro de diálogo se adjunta automáticamente a la `CDialogImpl` objeto. Para crear un cuadro de diálogo modal, llame a [DoModal](#domodal). El segundo reemplazo anterior solo se usa con [CComControl](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>  CDialogImpl::DestroyWindow

Destruye un cuadro de diálogo no modal.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el cuadro de diálogo se destruyó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Devuelve TRUE si el cuadro de diálogo se destruyó correctamente; en caso contrario, FALSE.

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
[in] El identificador para el cuadro de diálogo.

*uMsg*<br/>
[in] El mensaje enviado al cuadro de diálogo.

*wParam*<br/>
[in] Información adicional específica del mensaje.

*lParam*<br/>
[in] Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

TRUE si se procesa el mensaje; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

`DialogProc` el mapa de mensajes de forma predeterminada se usa para dirigir mensajes a los controladores adecuados.

Puede invalidar `DialogProc` para proporcionar un mecanismo diferente para el tratamiento de mensajes.

##  <a name="domodal"></a>  CDialogImpl::DoModal

Crea un cuadro de diálogo modal.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
[in] El identificador de la ventana propietaria. El valor predeterminado es el valor devuelto de la [GetActiveWindow](/windows/desktop/api/winuser/nf-winuser-getactivewindow) función de Win32.

*dwInitParam*<br/>
[in] Especifica el valor para pasar al cuadro de diálogo en el *lParam* parámetro del mensaje WM_INITDIALOG.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el valor de la *nRetCode* los parámetros especificados en la llamada a [EndDialog](#enddialog). En caso contrario, es -1.

### <a name="remarks"></a>Comentarios

Este cuadro de diálogo se adjunta automáticamente a la `CDialogImpl` objeto.

Para crear un cuadro de diálogo no modal, llame a [crear](#create).

##  <a name="enddialog"></a>  CDialogImpl::EndDialog

Destruye un cuadro de diálogo modal.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parámetros

*nRetCode*<br/>
[in] El valor que va a devolver [CDialogImpl::DoModal](#domodal).

### <a name="return-value"></a>Valor devuelto

TRUE si se destruye el cuadro de diálogo; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

`EndDialog` debe llamarse a través del procedimiento de cuadro de diálogo. Después de que se destruye el cuadro de diálogo, Windows utiliza el valor de *nRetCode* como el valor devuelto para `DoModal`, que crea el cuadro de diálogo.

> [!NOTE]
>  No llame a `EndDialog` para destruir un cuadro de diálogo no modal. Llame a [API CWindow:: DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) en su lugar.

##  <a name="getdialogproc"></a>  CDialogImpl::GetDialogProc

Devuelve `DialogProc`, el procedimiento de cuadro de diálogo actual.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Valor devuelto

El procedimiento de cuadro de diálogo actual.

### <a name="remarks"></a>Comentarios

Invalide este método para reemplazar el procedimiento de cuadro de diálogo por los suyos propios.

##  <a name="mapdialogrect"></a>  CDialogImpl::MapDialogRect

Convierte unidades (maps) las unidades de cuadro de diálogo del rectángulo especificado a la pantalla (píxeles).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a un `CRect` objeto o [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura que va a recibir las coordenadas de cliente de la actualización que rodea la región de actualización.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la actualización se realiza correctamente; 0 si se produce un error en la actualización. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

### <a name="remarks"></a>Comentarios

La función reemplaza las coordenadas de la manera especificada `RECT` estructura con las coordenadas convertidas, lo que permite la estructura que se usará para crear un cuadro de diálogo o colocar un control dentro de un cuadro de diálogo.

##  <a name="onfinalmessage"></a>  CDialogImpl::OnFinalMessage

Se llama después de recibir el último mensaje (normalmente `WM_NCDESTROY`).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
[in] Identificador de la ventana que se va a destruir.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que si desea eliminar automáticamente el objeto tras la destrucción de ventanas, puede llamar a **eliminar este;** aquí.

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
[in] El identificador para el cuadro de diálogo.

*uMsg*<br/>
[in] El mensaje enviado al cuadro de diálogo.

*wParam*<br/>
[in] Información adicional específica del mensaje.

*lParam*<br/>
[in] Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

El procedimiento de ventana.

### <a name="remarks"></a>Comentarios

Después de la llamada inicial a `StartDialogProc`, `DialogProc` se establece como un procedimiento de cuadro de diálogo y aún más las llamadas ir ahí.

## <a name="see-also"></a>Vea también

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Información general de clases](../../atl/atl-class-overview.md)