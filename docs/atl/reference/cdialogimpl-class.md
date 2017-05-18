---
title: CDialogImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 76a95ed5c32b2125112b64ef4368e4a82f0acec0
ms.contentlocale: es-es
ms.lasthandoff: 03/31/2017

---
# <a name="cdialogimpl-class"></a>CDialogImpl (clase)
Esta clase proporciona métodos para crear un cuadro de diálogo modal o no modal.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
 
template <class T,  
    class TBase = CWindow>  
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>  
 
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `CDialogImpl`.  
  
 *TBase*  
 La clase base de la nueva clase. La clase base predeterminada es [CWindow](../../atl/reference/cwindow-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Crear](#create)|Crea un cuadro de diálogo no modal.|  
|[DestroyWindow](#destroywindow)|Destruye un cuadro de diálogo no modal.|  
|[DoModal](#domodal)|Crea un cuadro de diálogo modal.|  
|[EndDialog](#enddialog)|Destruye un cuadro de diálogo modal.|  
  
### <a name="cdialogimplbaset-methods"></a>Métodos de CDialogImplBaseT  
  
|||  
|-|-|  
|[GetDialogProc](#getdialogproc)|Devuelve el procedimiento de cuadro de diálogo actual.|  
|[MapDialogRect](#mapdialogrect)|Las unidades de cuadro de diálogo del rectángulo especificado se asigna a unidades de pantalla (píxeles).|  
|[OnFinalMessage](#onfinalmessage)|Llamado después de recibir el último mensaje, normalmente `WM_NCDESTROY`.|  
  
### <a name="static-functions"></a>Funciones estáticas  
  
|||  
|-|-|  
|[Función DialogProc](#dialogproc)|Procesa los mensajes enviados al cuadro de diálogo.|  
|[StartDialogProc](#startdialogproc)|Se llama cuando se recibe el primer mensaje para procesar los mensajes enviados al cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Con `CDialogImpl` puede crear un cuadro de diálogo modal o no modal. `CDialogImpl`proporciona el procedimiento de cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para dirigir mensajes a los controladores adecuados.  
  
 El destructor de clase base **~ CWindowImplRoot** garantiza que se ha pasado la ventana antes de destruir el objeto.  
  
 `CDialogImpl`se deriva de **CDialogImplBaseT**, que a su vez deriva de **CWindowImplRoot**.  
  
> [!NOTE]
>  La clase debe definir un **IDD** miembro que especifica el identificador de recurso de plantilla de cuadro de diálogo. Por ejemplo, el Asistente para proyectos ATL agrega automáticamente la siguiente línea a la clase:  
  
 [!code-cpp[NVC_ATL_Windowing #41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]  
  
 donde `MyDlg` es el **nombre corto** especificadas en el asistente **nombres** página.  
  
|Para obtener más información sobre|Vea|  
|--------------------------------|---------|  
|Crear controles|[Tutorial ATL](../../atl/active-template-library-atl-tutorial.md)|  
|Con cuadros de diálogo en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|  
|Asistente para proyectos ATL|[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|  
|Cuadros de diálogo|[Cuadros de diálogo](http://msdn.microsoft.com/library/windows/desktop/ms632588) y los temas siguientes en la[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="create"></a>CDialogImpl::Create  
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
 `hWndParent`  
 [in] El identificador de la ventana propietaria.  
  
 **RECT SIGUIENTE**`rect`  
 [in] A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura especificando el cuadro de diálogo tamaño y posición.  
  
 `dwInitParam`  
 [in] Especifica el valor que debe pasarse al cuadro de diálogo en el **lParam** parámetro de la **WM_INITDIALOG** mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador para el cuadro de diálogo recién creado.  
  
### <a name="remarks"></a>Comentarios  
 Este cuadro de diálogo se adjunta automáticamente a la `CDialogImpl` objeto. Para crear un cuadro de diálogo modal, llame a [DoModal](#domodal). El segundo invalidación sólo se utiliza con [CComControl](../../atl/reference/ccomcontrol-class.md).  
  
##  <a name="destroywindow"></a>CDialogImpl::DestroyWindow  
 Destruye un cuadro de diálogo no modal.  
  
```  
 
BOOL DestroyWindow();

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el cuadro de diálogo se destruyen correctamente; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **TRUE** si el cuadro de diálogo se destruyen correctamente; en caso contrario **FALSE**.  
  
##  <a name="dialogproc"></a>CDialogImpl::DialogProc  
 Esta función estática implementa el procedimiento de cuadro de diálogo.  
  
```  
 
static LRESULT CALLBACK DialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam);

 
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 [in] El identificador para el cuadro de diálogo.  
  
 `uMsg`  
 [in] El mensaje enviado al cuadro de diálogo.  
  
 `wParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
 `lParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el mensaje se procesó; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 `DialogProc`utiliza la asignación de mensaje predeterminado para dirigir los mensajes a los controladores adecuados.  
  
 Puede invalidar `DialogProc` para proporcionar un mecanismo diferente para el tratamiento de mensajes.  
  
##  <a name="domodal"></a>CDialogImpl::DoModal  
 Crea un cuadro de diálogo modal.  
  
```   
INT_PTR DoModal(  
    HWND hWndParent = ::GetActiveWindow(),   
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 [in] El identificador de la ventana propietaria. El valor predeterminado es el valor devuelto de la [GetActiveWindow](http://msdn.microsoft.com/library/windows/desktop/ms646292) función de Win32.  
  
 `dwInitParam`  
 [in] Especifica el valor que debe pasarse al cuadro de diálogo en el **lParam** parámetro de la **WM_INITDIALOG** mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el valor de la `nRetCode` los parámetros especificados en la llamada a [EndDialog](#enddialog). En caso contrario, devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Este cuadro de diálogo se adjunta automáticamente a la `CDialogImpl` objeto.  
  
 Para crear un cuadro de diálogo no modal, llame a [crear](#create).  
  
##  <a name="enddialog"></a>CDialogImpl::EndDialog  
 Destruye un cuadro de diálogo modal.  
  
```   
BOOL EndDialog(int nRetCode); 
```  
  
### <a name="parameters"></a>Parámetros  
 `nRetCode`  
 [in] El valor que va a devolver [CDialogImpl::DoModal](#domodal).  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el cuadro de diálogo es destruido; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 `EndDialog`se debe llamar a través del procedimiento de cuadro de diálogo. Después de que se destruya el cuadro de diálogo, Windows utiliza el valor de `nRetCode` como el valor devuelto para `DoModal`, que crea el cuadro de diálogo.  
  
> [!NOTE]
>  No llame a `EndDialog` para destruir un cuadro de diálogo no modal. Llame a [API CWindow:: DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) en su lugar.  
  
##  <a name="getdialogproc"></a>CDialogImpl::GetDialogProc  
 Devuelve `DialogProc`, el procedimiento de cuadro de diálogo actual.  
  
```   
virtual WNDPROC GetDialogProc(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El procedimiento de cuadro de diálogo actual.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para reemplazar el procedimiento de cuadro de diálogo por los suyos propios.  
  
##  <a name="mapdialogrect"></a>CDialogImpl::MapDialogRect  
 Convierte las unidades de cuadro de diálogo del rectángulo especificado a la pantalla (maps) unidades (píxeles).  
  
```   
BOOL MapDialogRect(LPRECT lpRect); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un `CRect` objeto o [RECT](../../mfc/reference/rect-structure1.md) estructura que va a recibir las coordenadas de cliente de la actualización que rodea la región de actualización.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la actualización se realiza correctamente; 0 si se produce un error en la actualización. Para obtener información de errores extendida, realice una llamada a `GetLastError`.  
  
### <a name="remarks"></a>Comentarios  
 La función reemplaza las coordenadas de la manera especificada `RECT` estructura con las coordenadas convertidas, lo que permite la estructura que se usará para crear un cuadro de diálogo o la posición de un control dentro de un cuadro de diálogo.  
  
##  <a name="onfinalmessage"></a>CDialogImpl::OnFinalMessage  
 Llamado después de recibir el último mensaje (normalmente `WM_NCDESTROY`).  
  
```   
virtual void OnFinalMessage(HWND hWnd); 
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 [in] Identificador de la ventana que se destruya.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que si desea eliminar automáticamente el objeto tras la destrucción de ventanas, puede llamar a `delete this;` aquí.  
  
##  <a name="startdialogproc"></a>CDialogImpl::StartDialogProc  
 Se llama solo una vez, cuando se recibe el primer mensaje, para procesar mensajes enviados al cuadro de diálogo.  
  
```   
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam); 
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 [in] El identificador para el cuadro de diálogo.  
  
 `uMsg`  
 [in] El mensaje enviado al cuadro de diálogo.  
  
 `wParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
 `lParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
### <a name="return-value"></a>Valor devuelto  
 El procedimiento de ventana.  
  
### <a name="remarks"></a>Comentarios  
 Después de la llamada inicial a `StartDialogProc`, `DialogProc` se establece como un procedimiento de cuadro de diálogo y más llamadas dirigirse a estos.  
  
## <a name="see-also"></a>Vea también  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [Información general de clases](../../atl/atl-class-overview.md)
