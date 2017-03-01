---
title: Clase CMFCDesktopAlertWnd | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWnd
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWnd class
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
caps.latest.revision: 33
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
ms.openlocfilehash: be9d81ffff003119aa7ff9e0cd100c575bd82d36
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class
La `CMFCDesktopAlertWnd` clase implementa la funcionalidad de un cuadro de diálogo no modal que aparece en la pantalla para informar al usuario sobre un evento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCDesktopAlertWnd::Create](#create)|Crea e inicializa la ventana de alerta de escritorio.|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Devuelve la velocidad de animación.|  
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Devuelve el tipo de animación.|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Devuelve el tiempo de espera de cierre automático.|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Devuelve el alto del título.|  
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||  
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Devuelve la última posición válida de la ventana de alerta de escritorio en la pantalla.|  
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Devuelve el nivel de transparencia.|  
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Determina si se muestra la ventana de alerta de escritorio con título pequeño.|  
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Lo llama el marco de trabajo cuando el usuario hace clic en un botón de vínculo que se encuentra en el menú alerta de escritorio.|  
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|El marco de trabajo llama a esta función miembro cuando el usuario selecciona un elemento en un menú, cuando un control secundario envía un mensaje de notificación, o cuando se traduce una pulsación de tecla de aceleración. (Invalida [CWnd:: OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|  
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||  
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Establece la velocidad de animación de nuevo.|  
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Establece el tipo de animación.|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Establece el tiempo de espera de cierre automático.|  
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Cambia entre los títulos pequeños y normales.|  
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|Establece el nivel de transparencia.|  
  
## <a name="remarks"></a>Comentarios  
 Una ventana de alerta de escritorio puede ser transparente, puede aparecer con efectos de animación y puede desaparecer (después de un retraso especificado o cuando el usuario lo cierra haciendo clic en el botón de cierre).  
  
 Una ventana de alerta de escritorio también puede contener un cuadro de diálogo predeterminado que a su vez contiene un icono, el texto del mensaje (una etiqueta) y un vínculo. Como alternativa, una ventana de alerta de escritorio puede contener un cuadro de diálogo personalizado de recursos de la aplicación.  
  
 Crear una ventana de alerta de escritorio en dos pasos. En primer lugar, llame al constructor para construir la `CMFCDesktopAlertWnd` objeto. En segundo lugar, llame a la [CMFCDesktopAlertWnd::Create](#create) función de miembro para crear la ventana y adjuntarlo a la `CMFCDesktopAlertWnd` objeto.  
  
 La `CMFCDesktopAlertWnd` objeto crea un cuadro de diálogo secundarios especiales que rellena el área de cliente de la ventana de alerta de escritorio. El cuadro de diálogo posee todos los controles que se colocan en él.  
  
 Para mostrar un cuadro de diálogo personalizado en la ventana emergente, siga estos pasos:  
  
1.  Derivar una clase de `CMFCDesktopAlertDialog`.  
  
2.  Crear una plantilla de cuadro de diálogo secundario en los recursos.  
  
3.  Llame a [CMFCDesktopAlertWnd::Create](#create) con el identificador de recurso de plantilla de cuadro de diálogo y un puntero a la información de clase en tiempo de ejecución de la clase derivada.  
  
4.  El cuadro de diálogo personalizado para controlar todas las notificaciones procedentes de los controles hospedados de programa o programar los controles hospedados controlar estas notificaciones directamente.  
  
 Utilice las siguientes funciones para controlar el comportamiento de la ventana de alerta de escritorio:  
  
-   Establece el tipo de animación mediante una llamada [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Las opciones válidas incluyen expandir, deslice y atenuación.  
  
-   Establecer la velocidad de fotogramas de animación llamando a [CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).  
  
-   Establecer el nivel de transparencia llamando [CMFCDesktopAlertWnd::SetTransparency](#settransparency).  
  
-   Cambiar el tamaño de la leyenda a pequeño llamando a [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). Título pequeño es 7 píxeles de alto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCDesktopAlertWnd` clase para configurar un `CMFCDesktopAlertWnd` objeto. El ejemplo muestra cómo establecer el tipo de animación, establecer la transparencia de la ventana emergente, especificar que la ventana de alerta muestra un título pequeño y establecer el tiempo que transcurre antes de que la ventana de alerta se cierra automáticamente. El ejemplo también muestra cómo crear e inicializar la ventana de alerta de escritorio. Este fragmento de código forma parte de la [ejemplo de demostración de alerta de escritorio](../../visual-cpp-samples.md).  
  
 [!code-cpp[1 NVC_MFC_DesktopAlertDemo](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxDesktopAlertWnd.h  
  
##  <a name="a-namecreatea--cmfcdesktopalertwndcreate"></a><a name="create"></a>CMFCDesktopAlertWnd::Create  
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
 [in] [out]`pWndOwner`  
 Especifica el propietario de la ventana de alerta. Propietario recibirá entonces todas las notificaciones de la ventana de alerta de escritorio. Este valor no puede ser `NULL`.  
  
 [in] `uiDlgResID`  
 Especifica el identificador de recurso de la ventana de alerta.  
  
 [in] `hMenu`  
 Especifica el menú que se muestra cuando el usuario hace clic en el botón de menú. Si `NULL`, no se muestra el botón de menú.  
  
 [in] `ptPos`  
 Especifica la posición inicial donde se muestra la ventana de alerta, utilizando las coordenadas de pantalla. Si este parámetro es (-1, -1), la ventana de alerta se muestra en la esquina inferior derecha de la pantalla.  
  
 [in] `pRTIDlgBar`  
 Información de clase en tiempo de ejecución para una clase de cuadro de diálogo personalizado que cubre el área de cliente de la ventana de alerta.  
  
 [in] `params`  
 Especifica los parámetros que se utilizan para crear una ventana de alerta.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana de alerta se creó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para crear una ventana de alerta. El área cliente de la ventana de alerta contiene un cuadro de diálogo secundario que aloja todos los controles que se muestran al usuario.  
  
 La primera sobrecarga del método crea una ventana de alerta que contiene un cuadro de diálogo secundario que se carga desde los recursos de la aplicación. La primera sobrecarga de método también puede especificar la información de clase en tiempo de ejecución para una clase de cuadro de diálogo personalizado.  
  
 La segunda sobrecarga del método crea una ventana de alerta que contiene los controles predeterminados. Puede especificar qué controles para mostrar modificando el [CMFCDesktopAlertWndInfo clase](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).  
  
##  <a name="a-namegetanimationspeeda--cmfcdesktopalertwndgetanimationspeed"></a><a name="getanimationspeed"></a>CMFCDesktopAlertWnd::GetAnimationSpeed  
 Devuelve la velocidad de animación.  
  
```  
UINT GetAnimationSpeed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La velocidad de animación de la ventana de alerta, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 ¿Con qué rapidez la ventana de alerta se abre y cierra describe la velocidad de animación.  
  
##  <a name="a-namegetanimationtypea--cmfcdesktopalertwndgetanimationtype"></a><a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType  
 Devuelve el tipo de animación.  
  
```  
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes tipos de animación:  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="a-namegetautoclosetimea--cmfcdesktopalertwndgetautoclosetime"></a><a name="getautoclosetime"></a>CMFCDesktopAlertWnd::GetAutoCloseTime  
 Devuelve el tiempo de espera de cierre automático.  
  
```  
int GetAutoCloseTime() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tiempo, en milisegundos, después del cual se cerrará automáticamente la ventana de alerta.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para determinar cuánto tiempo debe transcurrir antes de que la ventana de alerta se cerrará automáticamente.  
  
##  <a name="a-namegetcaptionheighta--cmfcdesktopalertwndgetcaptionheight"></a><a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight  
 Devuelve el alto del título.  
  
```  
virtual int GetCaptionHeight();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Alto, en píxeles, del título.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede invalidarse en una clase derivada. La implementación predeterminada cualquier: devuelve el valor de alto del título pequeño (7 píxeles) si debe mostrar la ventana emergente del título pequeño, o el valor obtenido con la función de la API de Windows `GetSystemMetrics(SM_CYSMCAPTION)`.  
  
##  <a name="a-namegetlastposa--cmfcdesktopalertwndgetlastpos"></a><a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos  
 Devuelve la última posición de la ventana de alerta de escritorio en la pantalla.  
  
```  
CPoint GetLastPos() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un punto en coordenadas de pantalla.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve la última posición válida de la ventana de alerta en la pantalla.  
  
##  <a name="a-namegettransparencya--cmfcdesktopalertwndgettransparency"></a><a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency  
 Devuelve el nivel de transparencia.  
  
```  
BYTE GetTransparency() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un nivel de transparencia entre 0 y 255, ambos inclusive. Cuanto mayor sea el valor, más opaco la ventana.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para recuperar el nivel de transparencia actual de la ventana de alerta.  
  
##  <a name="a-namehassmallcaptiona--cmfcdesktopalertwndhassmallcaption"></a><a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption  
 Determina si la ventana de alerta de escritorio tiene un título pequeño o un título de tamaño normal.  
  
```  
BOOL HasSmallCaption() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana emergente se muestra con un título pequeño; `FALSE` si la ventana emergente se muestra con un título de tamaño normal.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para determinar si la ventana emergente tiene un título pequeño o un título de tamaño normal. De forma predeterminada, el título pequeño es 7 píxeles de alto. Puede obtener el alto del título del tamaño normal mediante una llamada a la función API de Windows `GetSystemMetrics(SM_CYCAPTION)`.  
  
##  <a name="a-nameonbeforeshowa--cmfcdesktopalertwndonbeforeshow"></a><a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnBeforeShow(CPoint&);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CPoint&`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonclicklinkbuttona--cmfcdesktopalertwndonclicklinkbutton"></a><a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton  
 Lo llama el marco de trabajo cuando el usuario hace clic en un botón de vínculo que se encuentra en el menú alerta de escritorio.  
  
```  
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada si desea recibir una notificación cuando un usuario hace clic en el vínculo en la ventana de alerta.  
  
##  <a name="a-nameoncommanda--cmfcdesktopalertwndoncommand"></a><a name="oncommand"></a>CMFCDesktopAlertWnd::OnCommand  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnCommand(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `wParam`  
 [in] `lParam`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawa--cmfcdesktopalertwndondraw"></a><a name="ondraw"></a>CMFCDesktopAlertWnd::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameprocesscommanda--cmfcdesktopalertwndprocesscommand"></a><a name="processcommand"></a>CMFCDesktopAlertWnd::ProcessCommand  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL ProcessCommand(HWND hwnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hwnd`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetanimationspeeda--cmfcdesktopalertwndsetanimationspeed"></a><a name="setanimationspeed"></a>CMFCDesktopAlertWnd::SetAnimationSpeed  
 Establece la velocidad de animación de nuevo.  
  
```  
void SetAnimationSpeed(UINT nSpeed);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nSpeed`  
 Especifica la nueva velocidad de animación, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para establecer la velocidad de animación de la ventana de alerta. La velocidad de animación predeterminada es 30 milisegundos.  
  
##  <a name="a-namesetanimationtypea--cmfcdesktopalertwndsetanimationtype"></a><a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType  
 Establece el tipo de animación.  
  
```  
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `type`  
 Especifica el tipo de animación.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para establecer el tipo de animación. Puede especificar uno de los siguientes valores:  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="a-namesetautoclosetimea--cmfcdesktopalertwndsetautoclosetime"></a><a name="setautoclosetime"></a>CMFCDesktopAlertWnd::SetAutoCloseTime  
 Establece el tiempo de espera de cierre automático.  
  
```  
void SetAutoCloseTime(int nTime);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nTime`  
 El tiempo, en milisegundos, que transcurre antes de que la ventana de alerta se cierra automáticamente.  
  
### <a name="remarks"></a>Comentarios  
 La ventana de alerta se cierra automáticamente transcurrido el tiempo especificado, si el usuario no interactúa con la ventana.  
  
##  <a name="a-namesetsmallcaptiona--cmfcdesktopalertwndsetsmallcaption"></a><a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption  
 Cambia entre los títulos de tamaño pequeños y normal.  
  
```  
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSmallCaption`  
 `TRUE`para especificar que la ventana de alerta muestra un título pequeño; de lo contrario, `FALSE` para especificar que la ventana de alerta muestra una leyenda de tamaño normal.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para mostrar el título pequeño o de tamaño normal. De forma predeterminada, el título pequeño es 7 píxeles de alto. Puede obtener el tamaño de la leyenda regular llamando a la función API de Windows `GetSystemMetrics(SM_CYCAPTION)`.  
  
##  <a name="a-namesettransparencya--cmfcdesktopalertwndsettransparency"></a><a name="settransparency"></a>CMFCDesktopAlertWnd::SetTransparency  
 Establece el nivel de transparencia de la ventana emergente.  
  
```  
void SetTransparency(BYTE nTransparency);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nTransparency`  
 Especifica el nivel de transparencia. Este valor debe ser entre 0 y 255, ambos inclusive. Cuanto mayor sea el valor, más opaco la ventana.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para establecer el nivel de transparencia de la ventana emergente.  
  
##  <a name="a-namegetdialogsizea--cmfcdesktopalertwndgetdialogsize"></a><a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetDialogSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [Clase CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)

