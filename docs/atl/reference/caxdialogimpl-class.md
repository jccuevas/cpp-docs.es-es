---
title: Clase CAxDialogImpl
ms.date: 11/04/2016
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
ms.openlocfilehash: d8e60a817d197f67c14318a7d50ddf796e570142
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318737"
---
# <a name="caxdialogimpl-class"></a>Clase CAxDialogImpl

Esta clase implementa un cuadro de diálogo (modal o no modal) que hospeda controles ActiveX.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `CAxDialogImpl`de .

*TBase*<br/>
La clase de `CDialogImplBaseT`ventana base para .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Llame a este método para aconsejar o desaconsejar todas las entradas en el mapa de eventos de mapa de receptores del objeto.|
|[CAxDialogImpl::Crear](#create)|Llame a este método para crear un cuadro de diálogo no es posible.|
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Llame a este método para destruir un cuadro de diálogo no esmimoso.|
|[CAxDialogImpl::DoModal](#domodal)|Llame a este método para crear un cuadro de diálogo modal.|
|[CAxDialogImpl::EndDialog](#enddialog)|Llame a este método para destruir un cuadro de diálogo modal.|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Llame a este método para `DialogProc` obtener un puntero a la función de devolución de llamada.|
|[CAxDialogImpl::GetIDD](#getidd)|Llame a este método para obtener el identificador de recurso de plantilla de cuadro de diálogo|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Llame a este método para determinar si un mensaje está pensado para este cuadro de diálogo y, si lo es, procesar el mensaje.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAxDialogImpl::m_bModal](#m_bmodal)|Variable que solo existe en compilaciones de depuración y se establece en true si el cuadro de diálogo es modal.|

## <a name="remarks"></a>Observaciones

`CAxDialogImpl`le permite crear un cuadro de diálogo modal o no modal. `CAxDialogImpl`proporciona el procedimiento de cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para dirigir los mensajes a los controladores adecuados.

`CAxDialogImpl`deriva de `CDialogImplBaseT`, que a su vez deriva `CWindow`de `CMessageMap` *TBase* (de forma predeterminada, ) y .

La clase debe definir un miembro IDD que especifique el identificador de recurso de plantilla de cuadro de diálogo. Por ejemplo, al agregar un objeto de cuadro de diálogo ATL mediante el cuadro de diálogo **Agregar clase,** se agrega automáticamente la siguiente línea a la clase:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

donde `MyDialog` se encuentra el **nombre corto** introducido en el Asistente para cuadros de diálogo ATL.

Consulte [Implementación de un cuadro de diálogo](../../atl/implementing-a-dialog-box.md) para obtener más información.

Tenga en cuenta que un control ActiveX en un cuadro de diálogo modal creado con `CAxDialogImpl` no admitirá las teclas de aceleración. Para admitir claves de aceleración `CAxDialogImpl`en un cuadro de diálogo creado con , cree un cuadro de diálogo no informado y, utilizando su propio bucle de mensajes, utilice [CAxDialogImpl::IsDialogMessage](#isdialogmessage) después de obtener un mensaje de la cola para controlar una clave de acelerador.

Para obtener `CAxDialogImpl`más información sobre , consulte Preguntas frecuentes sobre la contención de [control ATL](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="caxdialogimpladvisesinkmap"></a><a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap

Llame a este método para aconsejar o desaconsejar todas las entradas en el mapa de eventos de mapa de receptores del objeto.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parámetros

*bAdvise*<br/>
Establezca en true si se deben avisar a todas las entradas del receptor; false si todas las entradas de sumidero deben ser desaconsejados.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="caxdialogimplcreate"></a><a name="create"></a>CAxDialogImpl::Crear

Llame a este método para crear un cuadro de diálogo no es posible.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
[en] El identificador de la ventana del propietario.

*dwInitParam*<br/>
[en] Especifica el valor que se va a pasar al cuadro de diálogo en el parámetro *lParam* del mensaje WM_INITDIALOG.

*RECT&*<br/>
Este parámetro no se utiliza. Este parámetro se `CComControl`pasa por .

### <a name="return-value"></a>Valor devuelto

El identificador del cuadro de diálogo recién creado.

### <a name="remarks"></a>Observaciones

Este cuadro de diálogo `CAxDialogImpl` se adjunta automáticamente al objeto. Para crear un cuadro de diálogo modal, llame a [DoModal](#domodal).

La segunda invalidación se proporciona solo para que los cuadros de diálogo se puedan utilizar con [CComControl](../../atl/reference/ccomcontrol-class.md).

## <a name="caxdialogimpldestroywindow"></a><a name="destroywindow"></a>CAxDialogImpl::DestroyWindow

Llame a este método para destruir un cuadro de diálogo no esmimoso.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Valor devuelto

TRUESi la ventana se destruye correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

No llame `DestroyWindow` para destruir un cuadro de diálogo modal. Llame a [EndDialog](#enddialog) en su lugar.

## <a name="caxdialogimpldomodal"></a><a name="domodal"></a>CAxDialogImpl::DoModal

Llame a este método para crear un cuadro de diálogo modal.

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

Si se realiza correctamente, el valor del parámetro *nRetCode* especificado en la llamada a [EndDialog](#enddialog); de lo contrario, -1.

### <a name="remarks"></a>Observaciones

Este cuadro de diálogo `CAxDialogImpl` se adjunta automáticamente al objeto.

Para crear un cuadro de diálogo no distingueso, llame a [Crear](#create).

## <a name="caxdialogimplenddialog"></a><a name="enddialog"></a>CAxDialogImpl::EndDialog

Llame a este método para destruir un cuadro de diálogo modal.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parámetros

*nRetCode*<br/>
[en] El valor que va a devolver [DoModal](#domodal).

### <a name="return-value"></a>Valor devuelto

TRUESi se destruye el cuadro de diálogo; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

`EndDialog`debe llamarse a través del procedimiento del cuadro de diálogo. Después de destruir el cuadro de diálogo, Windows utiliza el `DoModal`valor de *nRetCode* como valor devuelto para , que creó el cuadro de diálogo.

> [!NOTE]
> No llame `EndDialog` para destruir un cuadro de diálogo no codificador. Llame a [DestroyWindow](#destroywindow) en su lugar.

## <a name="caxdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc

Llame a este método para `DialogProc` obtener un puntero a la función de devolución de llamada.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero `DialogProc` a la función de devolución de llamada.

### <a name="remarks"></a>Observaciones

La `DialogProc` función es una función de devolución de llamada definida por la aplicación.

## <a name="caxdialogimplgetidd"></a><a name="getidd"></a>CAxDialogImpl::GetIDD

Llame a este método para obtener el identificador de recurso de plantilla de cuadro de diálogo.

```
int GetIDD();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de recurso de plantilla de cuadro de diálogo.

## <a name="caxdialogimplisdialogmessage"></a><a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage

Llame a este método para determinar si un mensaje está pensado para este cuadro de diálogo y, si lo es, procesar el mensaje.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Parámetros

*Pmsg*<br/>
Puntero a una estructura [MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene el mensaje que se va a comprobar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha procesado el mensaje, FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Este método está pensado para ser llamado desde dentro de un bucle de mensajes.

## <a name="caxdialogimplm_bmodal"></a><a name="m_bmodal"></a>CAxDialogImpl::m_bModal

Variable que solo existe en compilaciones de depuración y se establece en true si el cuadro de diálogo es modal.

```
bool m_bModal;
```

## <a name="see-also"></a>Consulte también

[CDialogImpl (clase)](../../atl/reference/cdialogimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
