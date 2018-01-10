---
title: Clase de CAxDialogImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2db97c0de9f262936212cf7f38abddf7c91eb5a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl (clase)
Esta clase implementa un cuadro de diálogo (modal o no modal) que hospeda los controles ActiveX.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T, class TBase = CWindow>  
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `CAxDialogImpl`.  
  
 *TBase*  
 La clase de ventana base para **CDialogImplBaseT**.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAxDialogImpl:: AdviseSinkMap](#advisesinkmap)|Llame a este método para notificar o no notificar todas las entradas de mapa de asignación de eventos de receptor del objeto.|  
|[CAxDialogImpl::Create](#create)|Llamar a este método para crear un cuadro de diálogo no modal.|  
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Llamar a este método para destruir un cuadro de diálogo no modal.|  
|[CAxDialogImpl::DoModal](#domodal)|Llamar a este método para crear un cuadro de diálogo modal.|  
|[CAxDialogImpl::EndDialog](#enddialog)|Llamar a este método para destruir el cuadro de diálogo modal.|  
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Llamar a este método para obtener un puntero a la `DialogProc` función de devolución de llamada.|  
|[CAxDialogImpl::GetIDD](#getidd)|Llamar a este método para obtener el identificador de recurso de plantilla de cuadro de diálogo|  
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Llamar a este método para determinar si un mensaje está destinado a este cuadro de diálogo y, si es así, procesar el mensaje.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CAxDialogImpl::m_bModal](#m_bmodal)|Una variable que existe solo en versiones de depuración se compila y se está establecida en true si el cuadro de diálogo es modal.|  
  
## <a name="remarks"></a>Comentarios  
 `CAxDialogImpl`permite crear un cuadro de diálogo modal o no modal. `CAxDialogImpl`proporciona el procedimiento de cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para dirigir mensajes a los controladores adecuados.  
  
 `CAxDialogImpl`se deriva de `CDialogImplBaseT`, que a su vez deriva de *TBase* (de forma predeterminada, `CWindow`) y `CMessageMap`.  
  
 La clase debe definir a un miembro IDD que especifica el identificador de recurso de plantilla de cuadro de diálogo. Por ejemplo, al agregar un objeto de cuadro de diálogo ATL mediante el **Agregar clase** cuadro de diálogo agrega automáticamente la siguiente línea a la clase:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]  
  
 donde `MyDialog` es el **nombre corto** especificadas en el Asistente de cuadro de diálogo ATL.  
  
 Vea [implementa un cuadro de diálogo](../../atl/implementing-a-dialog-box.md) para obtener más información.  
  
 Tenga en cuenta que un control ActiveX en un cuadro de diálogo modal creado con `CAxDialogImpl` no admitirá las teclas de aceleración. Para admitir las teclas de aceleración en un cuadro de diálogo creado con `CAxDialogImpl`, cree un cuadro de diálogo no modal y, con su propio bucle de mensajes, usar [CAxDialogImpl::IsDialogMessage](#isdialogmessage) después de recibir un mensaje de la cola para controlar un tecla de aceleración.  
  
 Para obtener más información sobre `CAxDialogImpl`, consulte [preguntas más frecuentes sobre contención de Control de ATL](../../atl/atl-control-containment-faq.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CDialogImplBaseT`  
  
 `CAxDialogImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="advisesinkmap"></a>CAxDialogImpl:: AdviseSinkMap  
 Llame a este método para notificar o no notificar todas las entradas de mapa de asignación de eventos de receptor del objeto.  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>Parámetros  
 `bAdvise`  
 Se establece en true si todas las entradas de receptor son recibir información; entradas de False si todos los receptores son desaconsejarán.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="create"></a>CAxDialogImpl::Create  
 Llamar a este método para crear un cuadro de diálogo no modal.  
  
```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 [in] El identificador de la ventana propietaria.  
  
 `dwInitParam`  
 [in] Especifica el valor que debe pasarse al cuadro de diálogo en el `lParam` parámetro de la **WM_INITDIALOG** mensaje.  
  
 **RECT &**  
 Este parámetro no se utiliza. Este parámetro se pasa `CComControl`.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador para el cuadro de diálogo recién creado.  
  
### <a name="remarks"></a>Comentarios  
 Este cuadro de diálogo se adjunta automáticamente a la `CAxDialogImpl` objeto. Para crear un cuadro de diálogo modal, llame a [DoModal](#domodal).  
  
 La invalidación de segundo se proporciona sólo para cuadros de diálogo se puedan utilizar con [CComControl](../../atl/reference/ccomcontrol-class.md).  
  
##  <a name="destroywindow"></a>CAxDialogImpl::DestroyWindow  
 Llamar a este método para destruir un cuadro de diálogo no modal.  
  
```
BOOL DestroyWindow();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana se destruyó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 No llame a `DestroyWindow` para destruir el cuadro de diálogo modal. Llame a [EndDialog](#enddialog) en su lugar.  
  
##  <a name="domodal"></a>CAxDialogImpl::DoModal  
 Llamar a este método para crear un cuadro de diálogo modal.  
  
```
INT_PTR DoModal(
  HWND hWndParent = ::GetActiveWindow(), 
  LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 [in] El identificador de la ventana propietaria. El valor predeterminado es el valor devuelto de la [GetActiveWindow](http://msdn.microsoft.com/library/windows/desktop/ms646292) función de Win32.  
  
 `dwInitParam`  
 [in] Especifica el valor que debe pasarse al cuadro de diálogo en el `lParam` parámetro de la **WM_INITDIALOG** mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el valor de la `nRetCode` los parámetros especificados en la llamada a [EndDialog](#enddialog); en caso contrario, -1.  
  
### <a name="remarks"></a>Comentarios  
 Este cuadro de diálogo se adjunta automáticamente a la `CAxDialogImpl` objeto.  
  
 Para crear un cuadro de diálogo no modal, llame a [crear](#create).  
  
##  <a name="enddialog"></a>CAxDialogImpl::EndDialog  
 Llamar a este método para destruir el cuadro de diálogo modal.  
  
```
BOOL EndDialog(int nRetCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nRetCode`  
 [in] El valor que va a devolver [DoModal](#domodal).  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el cuadro de diálogo se destruye; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 `EndDialog`se debe llamar mediante el procedimiento de cuadro de diálogo. Después de que se destruya el cuadro de diálogo, Windows utiliza el valor de `nRetCode` como el valor devuelto para `DoModal`, que crea el cuadro de diálogo.  
  
> [!NOTE]
>  No llame a `EndDialog` para destruir un cuadro de diálogo no modal. Llame a [DestroyWindow](#destroywindow) en su lugar.  
  
##  <a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc  
 Llamar a este método para obtener un puntero a la `DialogProc` función de devolución de llamada.  
  
```
virtual DLGPROC GetDialogProc();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la `DialogProc` función de devolución de llamada.  
  
### <a name="remarks"></a>Comentarios  
 El `DialogProc` trata de una función de devolución de llamada definida por la aplicación.  
  
##  <a name="getidd"></a>CAxDialogImpl::GetIDD  
 Llamar a este método para obtener el identificador de recurso de plantilla de cuadro de diálogo.  
  
```
int GetIDD();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador de recurso de plantilla de cuadro de diálogo.  
  
##  <a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage  
 Llamar a este método para determinar si un mensaje está destinado a este cuadro de diálogo y, si es así, procesar el mensaje.  
  
```
BOOL IsDialogMessage(LPMSG pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMsg`  
 Puntero a un [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) estructura que contiene el mensaje que se va a comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el mensaje se ha procesado, FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este método está pensado para ser llamado desde dentro de un bucle de mensajes.  
  
##  <a name="m_bmodal"></a>CAxDialogImpl::m_bModal  
 Una variable que existe solo en versiones de depuración se compila y se está establecida en true si el cuadro de diálogo es modal.  
  
```
bool m_bModal;
```  
  
## <a name="see-also"></a>Vea también  
 [CDialogImpl (clase)](../../atl/reference/cdialogimpl-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
