---
title: CDialogImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialogImpl
- ATL.CDialogImpl
- ATL::CDialogImpl
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 732227ef8566ce5e2985a3e65a1153a130df6b20
ms.lasthandoff: 02/24/2017

---
# <a name="cdialogimpl-class"></a>CDialogImpl (clase)
Esta clase proporciona métodos para crear un cuadro de diálogo modal o no modal.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
|[MapDialogRect](#mapdialogrect)|Asigna las unidades de cuadro de diálogo del rectángulo especificado en unidades de pantalla (píxeles).|  
|[OnFinalMessage](#onfinalmessage)|Llamado después de recibir el último mensaje, normalmente `WM_NCDESTROY`.|  
  
### <a name="static-functions"></a>Funciones estáticas  
  
|||  
|-|-|  
|[DialogProc](#dialogproc)|Procesa los mensajes enviados al cuadro de diálogo.|  
|[StartDialogProc](#startdialogproc)|Se llama cuando se recibe el primer mensaje para procesar los mensajes enviados al cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Con `CDialogImpl` puede crear un cuadro de diálogo modal o no modal. `CDialogImpl`proporciona el procedimiento de cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para dirigir mensajes a los controladores adecuados.  
  
 El destructor de clase base **~ CWindowImplRoot** garantiza que se ha eliminado la ventana antes de destruir el objeto.  
  
 `CDialogImpl`se deriva de **CDialogImplBaseT**, que a su vez deriva de **CWindowImplRoot**.  
  
> [!NOTE]
>  La clase se debe definir una **IDD** miembro que especifica el identificador de recurso de plantilla de cuadro de diálogo. Por ejemplo, el Asistente para proyectos ATL agrega automáticamente la línea siguiente a la clase:  
  
 [!code-cpp[NVC_ATL_Windowing nº&41;](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]  
  
 donde `MyDlg` es el **nombre corto** especificada en el asistente **nombres** página.  
  
|Para obtener más información sobre|Vea|  
|--------------------------------|---------|  
|Crear controles|[Tutorial ATL](../../atl/active-template-library-atl-tutorial.md)|  
|Con cuadros de diálogo en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|  
|Asistente para proyectos ATL|[Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|  
|Cuadros de diálogo|[Cuadros de diálogo](http://msdn.microsoft.com/library/windows/desktop/ms632588) y los temas siguientes en la[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="a-namecreatea--cdialogimplcreate"></a><a name="create"></a>CDialogImpl::Create  
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
  
 **RECT ASPECTO**`rect`  
 [in] Un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que especifica el cuadro de diálogo tamaño y posición.  
  
 `dwInitParam`  
 [in] Especifica el valor para pasar al cuadro de diálogo en el **lParam** parámetro de la **WM_INITDIALOG** mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador para el cuadro de diálogo recién creado.  
  
### <a name="remarks"></a>Comentarios  
 Este cuadro de diálogo se adjunta automáticamente a la `CDialogImpl` objeto. Para crear un cuadro de diálogo modal, llame a [DoModal](#domodal). El segundo reemplazo anterior sólo se utiliza con [CComControl](../../atl/reference/ccomcontrol-class.md).  
  
##  <a name="a-namedestroywindowa--cdialogimpldestroywindow"></a><a name="destroywindow"></a>CDialogImpl::DestroyWindow  
 Destruye un cuadro de diálogo no modal.  
  
```  
 
BOOL DestroyWindow();

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el cuadro de diálogo se ha destruido correctamente; de lo contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **TRUE** si el cuadro de diálogo se ha destruido correctamente; de lo contrario **FALSE**.  
  
##  <a name="a-namedialogproca--cdialogimpldialogproc"></a><a name="dialogproc"></a>CDialogImpl::DialogProc  
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
 **TRUE** si el mensaje se procesa; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 `DialogProc`utiliza el mapa de mensajes predeterminado para dirigir mensajes a los controladores adecuados.  
  
 Puede reemplazar `DialogProc` para proporcionar un mecanismo diferente para el tratamiento de mensajes.  
  
##  <a name="a-namedomodala--cdialogimpldomodal"></a><a name="domodal"></a>CDialogImpl::DoModal  
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
 [in] Especifica el valor para pasar al cuadro de diálogo en el **lParam** parámetro de la **WM_INITDIALOG** mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el valor de la `nRetCode` los parámetros especificados en la llamada a [EndDialog](#enddialog). En caso contrario, es -1.  
  
### <a name="remarks"></a>Comentarios  
 Este cuadro de diálogo se adjunta automáticamente a la `CDialogImpl` objeto.  
  
 Para crear un cuadro de diálogo no modal, llame a [crear](#create).  
  
##  <a name="a-nameenddialoga--cdialogimplenddialog"></a><a name="enddialog"></a>CDialogImpl::EndDialog  
 Destruye un cuadro de diálogo modal.  
  
```   
BOOL EndDialog(int nRetCode); 
```  
  
### <a name="parameters"></a>Parámetros  
 `nRetCode`  
 [in] El valor devuelto por [CDialogImpl::DoModal](#domodal).  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el cuadro de diálogo es destruido; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 `EndDialog`se debe llamar a través del procedimiento de cuadro de diálogo. Después de que se destruya el cuadro de diálogo, Windows utiliza el valor de `nRetCode` como el valor devuelto para `DoModal`, que crea el cuadro de diálogo.  
  
> [!NOTE]
>  No llame a `EndDialog` para destruir un cuadro de diálogo no modal. Llame a [API CWindow:: DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) en su lugar.  
  
##  <a name="a-namegetdialogproca--cdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CDialogImpl::GetDialogProc  
 Devuelve `DialogProc`, el procedimiento de cuadro de diálogo actual.  
  
```   
virtual WNDPROC GetDialogProc(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El procedimiento de cuadro de diálogo actual.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para reemplazar el procedimiento de cuadro de diálogo por el suyo propio.  
  
##  <a name="a-namemapdialogrecta--cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a>CDialogImpl::MapDialogRect  
 Convierte las unidades de cuadro de diálogo del rectángulo especificado en pantalla (maps) unidades (píxeles).  
  
```   
BOOL MapDialogRect(LPRECT lpRect); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un `CRect` objeto o [RECT](../../mfc/reference/rect-structure1.md) estructura que va a recibir las coordenadas del cliente de la actualización que rodea la región de actualización.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la actualización se realiza correctamente; 0 si se produce un error en la actualización. Para obtener información de errores extendida, realice una llamada a `GetLastError`.  
  
### <a name="remarks"></a>Comentarios  
 La función reemplaza las coordenadas de la manera especificada `RECT` estructura con las coordenadas convertidas, lo que permite que la estructura que se usará para crear un cuadro de diálogo o la posición de un control dentro de un cuadro de diálogo.  
  
##  <a name="a-nameonfinalmessagea--cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a>CDialogImpl::OnFinalMessage  
 Llamado después de recibir el último mensaje (normalmente `WM_NCDESTROY`).  
  
```   
virtual void OnFinalMessage(HWND hWnd); 
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 [in] Identificador de la ventana que se va a destruir.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que si desea eliminar automáticamente el objeto tras la destrucción de ventana, puede llamar a `delete this;` aquí.  
  
##  <a name="a-namestartdialogproca--cdialogimplstartdialogproc"></a><a name="startdialogproc"></a>CDialogImpl::StartDialogProc  
 Se llama sólo una vez, cuando se recibe el primer mensaje, para procesar mensajes enviados al cuadro de diálogo.  
  
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
 Después de la llamada inicial a `StartDialogProc`, `DialogProc` se establece como un procedimiento de cuadro de diálogo y demás llamadas ir ahí.  
  
## <a name="see-also"></a>Vea también  
 [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)   
 [Información general de la clase](../../atl/atl-class-overview.md)
