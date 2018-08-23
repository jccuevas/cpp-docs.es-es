---
title: Clase CMFCDesktopAlertWnd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09f086673ba015b168211261bed68db479ef77a9
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539695"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class
La `CMFCDesktopAlertWnd` clase implementa la funcionalidad de un cuadro de diálogo no modal que aparece en la pantalla para informar al usuario sobre un evento.  

 Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.    
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Cmfcdesktopalertwnd:: Create](#create)|Crea e inicializa la ventana de alerta de escritorio.|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Devuelve la velocidad de animación.|  
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Devuelve el tipo de animación.|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Devuelve el tiempo de espera de cierre automático.|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Devuelve el alto del título.|  
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||  
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Devuelve la última posición válida de la ventana de alerta de escritorio en la pantalla.|  
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Devuelve el nivel de transparencia.|  
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Determina si se muestra la ventana de alerta de escritorio con el título pequeño.|  
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Lo llama el marco cuando el usuario hace clic en un botón de vínculo que se encuentra en el menú de alerta de escritorio.|  
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|El marco de trabajo llama a esta función miembro cuando el usuario selecciona un elemento en un menú, cuando un control secundario envía un mensaje de notificación, o cuando se traduce una pulsación de tecla de aceleración. (Invalida [CWnd:: OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|  
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||  
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Establece la velocidad de animación de nuevo.|  
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Establece el tipo de animación.|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Establece el tiempo de espera de cierre automático.|  
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Cambia entre los títulos pequeños y normales.|  
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|Establece el nivel de transparencia.|  
  
## <a name="remarks"></a>Comentarios  
 Una ventana de alerta de escritorio puede ser transparente, puede aparecer con efectos de animación y lo puede desaparecer (después de un retraso especificado o cuando el usuario lo descarte haciendo clic en el botón de cierre).  
  
 Una ventana de alerta de escritorio también puede contener un cuadro de diálogo predeterminado que a su vez contiene un icono, el texto del mensaje (una etiqueta) y un vínculo. Como alternativa, una ventana de alerta de escritorio puede contener un cuadro de diálogo personalizado de recursos de la aplicación.  
  
 Crear una ventana de alerta de escritorio en dos pasos. En primer lugar, llame al constructor para construir el `CMFCDesktopAlertWnd` objeto. En segundo lugar, llame a la [cmfcdesktopalertwnd:: Create](#create) función miembro para crear la ventana y adjuntarlo a la `CMFCDesktopAlertWnd` objeto.  
  
 La `CMFCDesktopAlertWnd` objeto crea un cuadro de diálogo secundarios especiales que rellena el área de cliente de la ventana de alerta de escritorio. El cuadro de diálogo posee todos los controles que se colocan en él.  
  
 Para mostrar un cuadro de diálogo personalizado en la ventana emergente, siga estos pasos:  
  
1.  Derivar una clase de `CMFCDesktopAlertDialog`.  
  
2.  Crear una plantilla de cuadro de diálogo secundarios en los recursos.  
  
3.  Llame a [cmfcdesktopalertwnd:: Create](#create) con el identificador de recurso de la plantilla de cuadro de diálogo y un puntero a la información de clase en tiempo de ejecución de la clase derivada.  
  
4.  Programar el cuadro de diálogo personalizado para controlar todas las notificaciones que proceden de los controles hospedados o programar los controles hospedados para tratar directamente estas notificaciones.  
  
 Utilice las siguientes funciones para controlar el comportamiento de la ventana de alerta de escritorio:  
  
-   Establezca el tipo de animación mediante una llamada a [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Las opciones válidas incluyen expandir, deslice y atenuar.  
  
-   Establecer la velocidad de fotogramas de animación mediante una llamada a [CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).  
  
-   Establecer el nivel de transparencia mediante una llamada a [CMFCDesktopAlertWnd::SetTransparency](#settransparency).  
  
-   Cambiar el tamaño de la leyenda a pequeño mediante una llamada a [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). El título pequeño es 7 píxeles de alto.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo usar varios métodos en el `CMFCDesktopAlertWnd` clase para configurar un `CMFCDesktopAlertWnd` objeto. El ejemplo muestra cómo establecer el tipo de animación, la transparencia de la ventana emergente, especifique que la ventana de alerta muestra un título pequeño y el tiempo que transcurre antes de la ventana de alerta se cierra automáticamente. El ejemplo también muestra cómo crear e inicializar la ventana de alerta de escritorio. Este fragmento de código forma parte de la [ejemplo de demostración de alerta de escritorio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxDesktopAlertWnd.h  
  
##  <a name="create"></a>  Cmfcdesktopalertwnd:: Create  
 Crea e inicializa la ventana de alerta de escritorio.  
  
```  
virtual BOOL Create(
    CWnd* pWndOwner,  
    UINT uiDlgResID,  
    HMENU hMenu = NULL,  
    CPoint ptPos = CPoint(-1,-1),  
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

 
virtual BOOL Create(
    CWnd* pWndOwner,  
    CMFCDesktopAlertWndInfo& params,  
    HMENU hMenu = NULL,  
    CPoint ptPos = CPoint(-1,-1));
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out] *pWndOwner*  
 Especifica el propietario de la ventana de alerta. Ese propietario, a continuación, recibirá todas las notificaciones de la ventana de alerta de escritorio. Este valor no puede ser NULL.  
  
 [in] *uiDlgResID*  
 Especifica el identificador de recurso de la ventana de alerta.  
  
 [in] *hMenu*  
 Especifica el menú que aparece cuando el usuario hace clic en el botón de menú. Si es NULL, no se muestra el botón de menú.  
  
 [in] *ptPos*  
 Especifica la posición inicial donde se muestra la ventana de alerta, utilizando las coordenadas de pantalla. Si este parámetro es (-1, -1), la ventana de alerta se muestra en la esquina inferior derecha de la pantalla.  
  
 [in] *pRTIDlgBar*  
 Información de clase en tiempo de ejecución para una clase de cuadro de diálogo personalizado que cubre el área de cliente de la ventana de alerta.  
  
 [in] *params*  
 Especifica los parámetros que se usan para crear una ventana de alerta.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana de alerta se creó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para crear una ventana de alerta. El área cliente de la ventana de alerta contiene un cuadro de diálogo secundario que hospeda todos los controles que se muestran al usuario.  
  
 La primera sobrecarga del método crea una ventana de alerta que contiene un cuadro de diálogo secundario que se carga desde los recursos de la aplicación. La primera sobrecarga del método también puede especificar la información de clase en tiempo de ejecución para una clase de cuadro de diálogo personalizados.  
  
 La segunda sobrecarga del método crea una ventana de alerta que contiene los controles predeterminados. Puede especificar qué controles para mostrar modificando el [clase CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).  
  
##  <a name="getanimationspeed"></a>  CMFCDesktopAlertWnd::GetAnimationSpeed  
 Devuelve la velocidad de animación.  
  
```  
UINT GetAnimationSpeed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La velocidad de animación de la ventana de alerta, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 La velocidad de animación describe rapidez abre la ventana de alerta y se cierra.  
  
##  <a name="getanimationtype"></a>  CMFCDesktopAlertWnd::GetAnimationType  
 Devuelve el tipo de animación.  
  
```  
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes tipos de animación:  
  
- NO_ANIMATION  
  
- EXPANDIR  
  
- DIAPOSITIVA  
  
- ATENUAR  
  
- SYSTEM_DEFAULT_ANIMATION  
  
##  <a name="getautoclosetime"></a>  CMFCDesktopAlertWnd::GetAutoCloseTime  
 Devuelve el tiempo de espera de cierre automático.  
  
```  
int GetAutoCloseTime() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tiempo, en milisegundos, después del cual se cerrará automáticamente la ventana de alerta.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para determinar cuánto tiempo debe transcurrir antes de la ventana de alerta se cerrará automáticamente.  
  
##  <a name="getcaptionheight"></a>  CMFCDesktopAlertWnd::GetCaptionHeight  
 Devuelve el alto del título.  
  
```  
virtual int GetCaptionHeight();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto, en píxeles, del título.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede invalidarse en una clase derivada. La implementación predeterminada cualquier: devuelve el valor del alto de título pequeño (7 píxeles) si debe mostrar la ventana emergente del título pequeño, o el valor obtenido de la función de la API de Windows `GetSystemMetrics(SM_CYSMCAPTION)`.  
  
##  <a name="getlastpos"></a>  CMFCDesktopAlertWnd::GetLastPos  
 Devuelve la última posición de la ventana de alerta de escritorio en la pantalla.  
  
```  
CPoint GetLastPos() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un punto en coordenadas de pantalla.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve la última posición válida de la ventana de alerta en la pantalla.  
  
##  <a name="gettransparency"></a>  CMFCDesktopAlertWnd::GetTransparency  
 Devuelve el nivel de transparencia.  
  
```  
BYTE GetTransparency() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un nivel de transparencia entre 0 y 255, ambos inclusive. Cuanto mayor sea el valor, el más opaco la ventana.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para recuperar el nivel de transparencia actual de la ventana de alerta.  
  
##  <a name="hassmallcaption"></a>  CMFCDesktopAlertWnd::HasSmallCaption  
 Determina si la ventana de alerta de escritorio tiene un título pequeño o un título de tamaño normal.  
  
```  
BOOL HasSmallCaption() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se muestra la ventana emergente con un título pequeño; FALSE si se muestra la ventana emergente con un título de tamaño normal.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para determinar si la ventana emergente tiene un título pequeño o un título de tamaño normal. De forma predeterminada, el título pequeño es 7 píxeles de alto. Puede obtener el alto de la leyenda de tamaño normal mediante una llamada a la función de la API de Windows `GetSystemMetrics(SM_CYCAPTION)`.  
  
##  <a name="onbeforeshow"></a>  CMFCDesktopAlertWnd::OnBeforeShow  

  
```  
virtual BOOL OnBeforeShow(CPoint&);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *CPoint &*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onclicklinkbutton"></a>  CMFCDesktopAlertWnd::OnClickLinkButton  
 Lo llama el marco cuando el usuario hace clic en un botón de vínculo que se encuentra en el menú de alerta de escritorio.  
  
```  
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *uiCmdID*  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada si desea recibir una notificación cuando un usuario hace clic en el vínculo en la ventana de alerta.  
  
##  <a name="oncommand"></a>  CMFCDesktopAlertWnd::OnCommand  

  
```  
virtual BOOL OnCommand(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wParam*  
 [in] *lParam*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondraw"></a>  CMFCDesktopAlertWnd::OnDraw  

  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="processcommand"></a>  CMFCDesktopAlertWnd::ProcessCommand  

  
```  
BOOL ProcessCommand(HWND hwnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *hwnd*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setanimationspeed"></a>  CMFCDesktopAlertWnd::SetAnimationSpeed  
 Establece la velocidad de animación de nuevo.  
  
```  
void SetAnimationSpeed(UINT nSpeed);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nSpeed*  
 Especifica la velocidad de animación de nuevo, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para establecer la velocidad de animación de la ventana de alerta. La velocidad de animación predeterminada es 30 milisegundos.  
  
##  <a name="setanimationtype"></a>  CMFCDesktopAlertWnd::SetAnimationType  
 Establece el tipo de animación.  
  
```  
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *tipo*  
 Especifica el tipo de animación.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para establecer el tipo de animación. Puede especificar uno de los siguientes valores:  
  
- NO_ANIMATION  
  
- EXPANDIR  
  
- DIAPOSITIVA  
  
- ATENUAR  
  
- SYSTEM_DEFAULT_ANIMATION  
  
##  <a name="setautoclosetime"></a>  CMFCDesktopAlertWnd::SetAutoCloseTime  
 Establece el tiempo de espera de cierre automático.  
  
```  
void SetAutoCloseTime(int nTime);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nintervalo de tiempo*  
 El tiempo, en milisegundos, que transcurre antes de que la ventana de alerta se cierra automáticamente.  
  
### <a name="remarks"></a>Comentarios  
 La ventana de alerta se cierra automáticamente transcurrido el tiempo especificado si el usuario no interactúa con la ventana.  
  
##  <a name="setsmallcaption"></a>  CMFCDesktopAlertWnd::SetSmallCaption  
 Cambia entre los títulos de tamaño pequeños y normal.  
  
```  
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bSmallCaption*  
 TRUE para especificar que la ventana de alerta muestra un título pequeño; de lo contrario, FALSE para especificar que la ventana de alerta muestra una leyenda de tamaño normal.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para mostrar el título pequeño o de tamaño normal. De forma predeterminada, el título pequeño es 7 píxeles de alto. Puede obtener el tamaño de la leyenda regular mediante una llamada a la función de la API de Windows `GetSystemMetrics(SM_CYCAPTION)`.  
  
##  <a name="settransparency"></a>  CMFCDesktopAlertWnd::SetTransparency  
 Establece el nivel de transparencia de la ventana emergente.  
  
```  
void SetTransparency(BYTE nTransparency);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nTransparency*  
 Especifica el nivel de transparencia. Este valor debe ser entre 0 y 255, ambos inclusive. Cuanto mayor sea el valor, el más opaco la ventana.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para establecer el nivel de transparencia de la ventana emergente.  
  
##  <a name="getdialogsize"></a>  CMFCDesktopAlertWnd::GetDialogSize  

  
```  
virtual CSize GetDialogSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWndInfo (clase)](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CMFCDesktopAlertDialog (clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)
