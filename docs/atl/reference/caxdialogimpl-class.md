---
title: CAxDialogImpl (clase)
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
ms.openlocfilehash: 548d2aed0644187b4b8dee1e472b581f1f92d6a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497667"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl (clase)

Esta clase implementa un cuadro de diálogo (modal o no modal) que hospeda controles ActiveX.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `CAxDialogImpl`.

*TBase*<br/>
Clase de ventana base para `CDialogImplBaseT`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Llame a este método para notificar o desaconsejar todas las entradas del mapa de eventos del mapa de receptores del objeto.|
|[CAxDialogImpl::Create](#create)|Llame a este método para crear un cuadro de diálogo no modal.|
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Llame a este método para destruir un cuadro de diálogo no modal.|
|[CAxDialogImpl::DoModal](#domodal)|Llame a este método para crear un cuadro de diálogo modal.|
|[CAxDialogImpl::EndDialog](#enddialog)|Llame a este método para destruir un cuadro de diálogo modal.|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Llame a este método para obtener un puntero a `DialogProc` la función de devolución de llamada.|
|[CAxDialogImpl::GetIDD](#getidd)|Llame a este método para obtener el identificador de recurso de plantilla de cuadro de diálogo|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Llame a este método para determinar si un mensaje está pensado para este cuadro de diálogo y, si es así, procesar el mensaje.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAxDialogImpl::m_bModal](#m_bmodal)|Una variable que solo existe en las compilaciones de depuración y está establecida en true si el cuadro de diálogo es modal.|

## <a name="remarks"></a>Comentarios

`CAxDialogImpl`permite crear un cuadro de diálogo modal o no modal. `CAxDialogImpl`proporciona el procedimiento de cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para dirigir los mensajes a los controladores adecuados.

`CAxDialogImpl`deriva de `CDialogImplBaseT`, que a su vez se deriva de *TBase* (de forma predeterminada `CWindow`,) `CMessageMap`y.

La clase debe definir un miembro de IDD que especifique el identificador de recurso de la plantilla de cuadro de diálogo. Por ejemplo, al agregar un objeto de cuadro de diálogo ATL mediante el cuadro de diálogo **Agregar clase** , se agrega automáticamente la siguiente línea a la clase:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

donde `MyDialog` es el **nombre corto** escrito en el Asistente para cuadros de diálogo ATL.

Vea [implementar un cuadro de diálogo](../../atl/implementing-a-dialog-box.md) para obtener más información.

Tenga en cuenta que un control ActiveX en un cuadro de diálogo `CAxDialogImpl` modal creado con no será compatible con las teclas de aceleración. Para admitir las teclas de aceleración de un cuadro de `CAxDialogImpl`diálogo creado con, cree un cuadro de diálogo no modal y, mediante su propio bucle de mensajes, use [CAxDialogImpl:: IsDialogMessage](#isdialogmessage) después de obtener un mensaje de la cola para controlar una tecla de aceleración.

Para obtener más información `CAxDialogImpl`sobre, vea [preguntas más frecuentes sobre contención de controles ATL](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

##  <a name="advisesinkmap"></a>  CAxDialogImpl::AdviseSinkMap

Llame a este método para notificar o desaconsejar todas las entradas del mapa de eventos del mapa de receptores del objeto.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parámetros

*bAdvise*<br/>
Establézcalo en true si se van a notificar todas las entradas de receptor; false si se van a desaconsejar todas las entradas del receptor.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="create"></a>  CAxDialogImpl::Create

Llame a este método para crear un cuadro de diálogo no modal.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
de Identificador de la ventana propietaria.

*dwInitParam*<br/>
de Especifica el valor que se va a pasar al cuadro de diálogo en el parámetro *lParam* del mensaje WM_INITDIALOG.

*RECT&*<br/>
Este parámetro no se utiliza. Este parámetro se pasa por `CComControl`.

### <a name="return-value"></a>Valor devuelto

Identificador del cuadro de diálogo que se acaba de crear.

### <a name="remarks"></a>Comentarios

Este cuadro de diálogo se adjunta automáticamente al `CAxDialogImpl` objeto. Para crear un cuadro de diálogo modal, llame a [DoModal](#domodal).

La segunda invalidación solo se proporciona, por lo que los cuadros de diálogo se pueden usar con [CComControl](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>  CAxDialogImpl::DestroyWindow

Llame a este método para destruir un cuadro de diálogo no modal.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana se destruye correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

No llame `DestroyWindow` a para destruir un cuadro de diálogo modal. En su lugar, llame a [EndDialog](#enddialog) .

##  <a name="domodal"></a>  CAxDialogImpl::DoModal

Llame a este método para crear un cuadro de diálogo modal.

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

Si es correcto, el valor del parámetro *nRetCode* especificado en la llamada a [EndDialog](#enddialog); de lo contrario,-1.

### <a name="remarks"></a>Comentarios

Este cuadro de diálogo se adjunta automáticamente al `CAxDialogImpl` objeto.

Para crear un cuadro de diálogo no modal, llame a [Create](#create).

##  <a name="enddialog"></a>  CAxDialogImpl::EndDialog

Llame a este método para destruir un cuadro de diálogo modal.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parámetros

*nRetCode*<br/>
de Valor que va a ser devuelto por [DoModal](#domodal).

### <a name="return-value"></a>Valor devuelto

TRUE si el cuadro de diálogo está destruido; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

`EndDialog`se debe llamar a mediante el procedimiento de cuadro de diálogo. Una vez destruido el cuadro de diálogo, Windows usa el valor de *nRetCode* como valor devuelto `DoModal`para, que creó el cuadro de diálogo.

> [!NOTE]
>  No llame `EndDialog` a para destruir un cuadro de diálogo no modal. En su lugar, llame a [DestroyWindow](#destroywindow) .

##  <a name="getdialogproc"></a>  CAxDialogImpl::GetDialogProc

Llame a este método para obtener un puntero a `DialogProc` la función de devolución de llamada.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la `DialogProc` función de devolución de llamada.

### <a name="remarks"></a>Comentarios

La `DialogProc` función es una función de devolución de llamada definida por la aplicación.

##  <a name="getidd"></a>  CAxDialogImpl::GetIDD

Llame a este método para obtener el identificador de recurso de la plantilla de cuadro de diálogo.

```
int GetIDD();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de recurso de la plantilla de cuadro de diálogo.

##  <a name="isdialogmessage"></a>  CAxDialogImpl::IsDialogMessage

Llame a este método para determinar si un mensaje está pensado para este cuadro de diálogo y, si es así, procesar el mensaje.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Parámetros

*pMsg*<br/>
Puntero a una estructura [MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene el mensaje que se va a comprobar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha procesado el mensaje; de lo contrario, devuelve FALSE.

### <a name="remarks"></a>Comentarios

Este método está pensado para ser llamado desde un bucle de mensajes.

##  <a name="m_bmodal"></a>  CAxDialogImpl::m_bModal

Una variable que solo existe en las compilaciones de depuración y está establecida en true si el cuadro de diálogo es modal.

```
bool m_bModal;
```

## <a name="see-also"></a>Vea también

[CDialogImpl (clase)](../../atl/reference/cdialogimpl-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
