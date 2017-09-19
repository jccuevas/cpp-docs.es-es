---
title: CPropertyPage (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPropertyPage
- AFXDLGS/CPropertyPage
- AFXDLGS/CPropertyPage::CPropertyPage
- AFXDLGS/CPropertyPage::CancelToClose
- AFXDLGS/CPropertyPage::Construct
- AFXDLGS/CPropertyPage::GetPSP
- AFXDLGS/CPropertyPage::OnApply
- AFXDLGS/CPropertyPage::OnCancel
- AFXDLGS/CPropertyPage::OnKillActive
- AFXDLGS/CPropertyPage::OnOK
- AFXDLGS/CPropertyPage::OnQueryCancel
- AFXDLGS/CPropertyPage::OnReset
- AFXDLGS/CPropertyPage::OnSetActive
- AFXDLGS/CPropertyPage::OnWizardBack
- AFXDLGS/CPropertyPage::OnWizardFinish
- AFXDLGS/CPropertyPage::OnWizardNext
- AFXDLGS/CPropertyPage::QuerySiblings
- AFXDLGS/CPropertyPage::SetModified
- AFXDLGS/CPropertyPage::m_psp
dev_langs:
- C++
helpviewer_keywords:
- property pages, CPropertyPage class
- dialog boxes, tabs
- CPropertyPage class
- tab dialog boxes
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: f14dfe29a6fa941192c2cfe792f16e4b032af941
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="cpropertypage-class"></a>CPropertyPage (clase)
Representa páginas individuales de una hoja de propiedades, también conocidas como cuadro de diálogo de pestaña.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPropertyPage : public CDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPropertyPage::CPropertyPage](#cpropertypage)|Construye un objeto `CPropertyPage`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPropertyPage::CancelToClose](#canceltoclose)|Cambia el botón Aceptar para cerrar de lectura y deshabilita el botón Cancelar, después de un cambio en la página de una hoja de propiedades modales irrecuperable.|  
|[CPropertyPage::Construct](#construct)|Construye un objeto `CPropertyPage`. Use `Construct` si desea especificar los parámetros en tiempo de ejecución, o si está utilizando matrices.|  
|[CPropertyPage::GetPSP](#getpsp)|Recupera las ventanas [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) estructura asociada con el `CPropertyPage` objeto.|  
|[CPropertyPage::OnApply](#onapply)|Llamado por el marco de trabajo cuando se hace clic en el botón Aplicar ahora.|  
|[CPropertyPage::OnCancel](#oncancel)|Llamado por el marco de trabajo cuando se hace clic en el botón Cancelar.|  
|[CPropertyPage:: OnKillActive](#onkillactive)|Llamado por el marco de trabajo cuando la página actual ya no es la página activa. Realizar la validación de datos aquí.|  
|[CPropertyPage::OnOK](#onok)|Llamado por el marco de trabajo cuando se hace clic en el Aceptar, aplicar ahora o botón Cerrar.|  
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Lo llama el marco cuando se hace clic en el botón Cancelar, y antes de que la cancelación ha llevado a cabo.|  
|[CPropertyPage::OnReset](#onreset)|Llamado por el marco de trabajo cuando se hace clic en el botón Cancelar.|  
|[Notificaciones CPropertyPage:: OnSetActive](#onsetactive)|Lo llama el marco cuando la página se realiza en la página activa.|  
|[CPropertyPage::OnWizardBack](#onwizardback)|Llamado por el marco de trabajo cuando se hace clic en el botón Atrás durante el uso de una hoja de propiedades de tipo asistente.|  
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Llamado por el marco de trabajo cuando se hace clic en el botón Finalizar al utilizar una hoja de propiedades de tipo asistente.|  
|[CPropertyPage::OnWizardNext](#onwizardnext)|Llamado por el marco de trabajo cuando se hace clic en el botón siguiente mientras utiliza una hoja de propiedades de tipo asistente.|  
|[CPropertyPage::QuerySiblings](#querysiblings)|Reenvía el mensaje a cada página de la hoja de propiedades.|  
|[CPropertyPage:: SetModified](#setmodified)|La llamada para activar o desactivar el botón Aplicar ahora.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPropertyPage::m_psp](#m_psp)|Las ventanas [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) estructura. Proporciona acceso a los parámetros de la página de propiedades básicas.|  
  
## <a name="remarks"></a>Comentarios  
 Como con cuadros de diálogo estándar, derive una clase de `CPropertyPage` para cada página en la hoja de propiedades. Usar `CPropertyPage`-objetos derivados, primero cree un [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) objeto y, a continuación, cree un objeto para cada página que va en la hoja de propiedades. Llame a [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) para cada página en la hoja y, a continuación, muestre la hoja de propiedades mediante una llamada a [CPropertySheet:: DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) para una hoja de propiedades modal, o [CPropertySheet:: Create](../../mfc/reference/cpropertysheet-class.md#create) para ver una hoja de propiedades no modal.  
  
 Puede crear un tipo de cuadro de diálogo de pestaña llamado a un asistente, que consta de una hoja de propiedades con una secuencia de páginas de propiedades que guía al usuario a través de los pasos necesarios para una operación, como configurar un dispositivo o crear un boletín. En un cuadro de diálogo de pestaña tipo de Asistente para las páginas de propiedades no tiene pestañas y solo una página de propiedades es visible a la vez. Además, en lugar de tener botones Aceptar y aplicar ahora, un cuadro de diálogo de pestaña de tipo asistente tiene un botón Atrás, un botón siguiente o finalizar y un botón de cancelación.  
  
 Para obtener más información acerca de cómo establecer una hoja de propiedades como un asistente, vea [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Para obtener más información sobre el uso de `CPropertyPage` objetos, vea el artículo [hojas de propiedades y páginas de propiedades](../../mfc/property-sheets-and-property-pages-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdlgs.h  
  
##  <a name="canceltoclose"></a>CPropertyPage::CancelToClose  
 Llame a esta función después de que se ha realizado un cambio irrecuperable a los datos en una página de una hoja de propiedades modales.  
  
```  
void CancelToClose();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función se debe cambiar el botón Aceptar para cerrar y deshabilitar el botón Cancelar. Este cambio no se puede cancelar el usuario que un cambio es permanente y las modificaciones de las alertas.  
  
 El `CancelToClose` función miembro no hace nada en una hoja de propiedades no modal, porque una hoja de propiedades no modal no tiene un botón de cancelación de forma predeterminada.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertyPage::QuerySiblings](#querysiblings).  
  
##  <a name="construct"></a>CPropertyPage::Construct  
 Llame a esta función miembro para construir un `CPropertyPage` objeto.  
  
```  
void Construct(
    UINT nIDTemplate,  
    UINT nIDCaption = 0);

 
void Construct(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption = 0);

 
void Construct(
    UINT nIDTemplate,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0);

 
void Construct(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDTemplate`  
 Id. de la plantilla usada para esta página.  
  
 `nIDCaption`  
 Identificador del nombre que se colocarán en la ficha para esta página. Si es 0, se van a realizar el nombre de la plantilla de cuadro de diálogo para esta página.  
  
 `lpszTemplateName`  
 Contiene una cadena terminada en null que es el nombre de un recurso de plantilla.  
  
 `nIDHeaderTitle`  
 Identificador del nombre que se colocarán en la ubicación del título del encabezado de página de propiedades. De manera predeterminada, es 0.  
  
 `nIDHeaderSubTitle`  
 Identificador del nombre que se colocarán en la ubicación del subtítulo del encabezado de página de propiedades. De manera predeterminada, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El objeto se muestra después de que se cumplen todas las condiciones siguientes:  
  
-   La página se ha agregado a una hoja de propiedades utilizando [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).  
  
-   La hoja de propiedades [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) o [crear](../../mfc/reference/cpropertysheet-class.md#create) función se ha llamado.  
  
-   El usuario ha seleccionado (con pestañas para) esta página.  
  
 Llame a **construir** si uno de los otros constructores de clase no se ha llamado. El `Construct` función miembro es flexible, ya que puede dejar en blanco la instrucción de parámetro y, a continuación, especificar varios parámetros y construcción en cualquier momento en el código.  
  
 Debe usar `Construct` cuando se trabaja con matrices, y debe llamar a **construir** por cada miembro de la matriz para que los miembros de datos se asignan los valores adecuados.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]  
  
##  <a name="cpropertypage"></a>CPropertyPage::CPropertyPage  
 Construye un objeto `CPropertyPage`.  
  
```  
CPropertyPage();

 
explicit CPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
explicit CPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
CPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
CPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDTemplate`  
 Id. de la plantilla usada para esta página.  
  
 `nIDCaption`  
 Identificador del nombre que se colocarán en la ficha para esta página. Si es 0, se van a realizar el nombre de la plantilla de cuadro de diálogo para esta página.  
  
 `dwSize`  
 `lpszTemplateName`  
 Apunta a una cadena que contiene el nombre de la plantilla para esta página. No puede ser **NULL**.  
  
 `nIDHeaderTitle`  
 Identificador del nombre que se colocarán en la ubicación del título del encabezado de página de propiedades.  
  
 `nIDHeaderSubTitle`  
 Identificador del nombre que se colocarán en la ubicación del subtítulo del encabezado de página de propiedades.  
  
### <a name="remarks"></a>Comentarios  
 El objeto se muestra después de que se cumplen todas las condiciones siguientes:  
  
-   La página se ha agregado a una hoja de propiedades utilizando [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).  
  
-   La hoja de propiedades [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) o [crear](../../mfc/reference/cpropertysheet-class.md#create) función se ha llamado.  
  
-   El usuario ha seleccionado (con pestañas para) esta página.  
  
 Si tiene varios parámetros (por ejemplo, si está utilizando una matriz), use [CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) en lugar de `CPropertyPage`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]  
  
##  <a name="getpsp"></a>CPropertyPage::GetPSP  
 Recupera las ventanas [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) estructura asociada con el `CPropertyPage` objeto.  
  
```  
const PROPSHEETPAGE& GetPSP() const;  
  
PROPSHEETPAGE& GetPSP();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la **PROPSHEETPAGE** estructura.  
  
##  <a name="m_psp"></a>CPropertyPage::m_psp  
 `m_psp`es una estructura cuyos miembros almacenan las características de [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548).  
  
```  
PROPSHEETPAGE m_psp;  
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta estructura para inicializar la apariencia de una página de propiedades después de se construye.  
  
 Para obtener más información sobre esta estructura, incluida una lista de sus miembros, vea **PROPSHEETPAGE** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]  
  
##  <a name="onapply"></a>CPropertyPage::OnApply  
 El marco de trabajo llama a esta función miembro cuando el usuario elige el el botón Aceptar o aplicar ahora.  
  
```  
virtual BOOL OnApply();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se aceptan los cambios; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el marco de trabajo llama a esta función, se aceptan los cambios realizados en todas las páginas de propiedades en la hoja de propiedades, la hoja de propiedades conserva el foco, y `OnApply` devuelve **TRUE** (el valor 1). Antes de `OnApply` puede llamarse mediante el marco de trabajo, debe haber llamado [SetModified](#setmodified) y establece su parámetro en **TRUE**. Esto activará el botón Aplicar ahora tan pronto como el usuario realiza un cambio en la página de propiedades.  
  
 Reemplace esta función miembro para especificar la acción realizada por el programa cuando el usuario hace clic en el botón Aplicar ahora. Al reemplazar el método, la función debe devolver **TRUE** para aceptar los cambios y **FALSE** para impedir que los cambios surten efecto.  
  
 La implementación predeterminada de `OnApply` llamadas `OnOK`.  
  
 Para obtener más información acerca de los mensajes de notificación se envía cuando el usuario presiona el aplicar ahora o botón Aceptar en una hoja de propiedades, vea [PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertyPage::OnOK](#onok).  
  
##  <a name="oncancel"></a>CPropertyPage::OnCancel  
 El marco de trabajo llama a esta función miembro cuando se selecciona el botón Cancelar.  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para llevar a cabo acciones al botón Cancelar. El valor predeterminado niega cualquier cambio que se han realizado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]  
  
##  <a name="onkillactive"></a>CPropertyPage:: OnKillActive  
 El marco de trabajo llama a esta función miembro cuando la página ya no es la página activa.  
  
```  
virtual BOOL OnKillActive();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si los datos se actualizan correctamente, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para llevar a cabo las tareas de validación de datos especiales.  
  
 La implementación predeterminada de esta función miembro copia los valores de los controles en la página de propiedades a las variables de miembro de la página de propiedades. Si los datos no se actualizan correctamente debido a un error de validación (DDV) de datos de cuadro de diálogo, la página conserva el foco.  
  
 Después de esta función miembro devuelve correctamente, el marco de trabajo llamará a la página [OnOK](#onok) función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]  
  
##  <a name="onok"></a>CPropertyPage::OnOK  
 El marco de trabajo llama a esta función miembro cuando el usuario elige Aceptar o en el botón Aplicar ahora, inmediatamente después de las llamadas de framework [OnKillActive](#onkillactive).  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario elige Aceptar o en el botón Aplicar ahora, el marco de trabajo recibe el [PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) recibir una notificación de la página de propiedades. La llamada a `OnOK` no se realizará si se llama a [CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) porque la página de propiedades no envía la notificación en ese caso.  
  
 Reemplace esta función miembro para implementar un comportamiento adicional específico a la página actualmente activa cuando el usuario cierra la hoja de propiedades completa.  
  
 La implementación predeterminada de esta función miembro marca como "limpiar" para reflejar que los datos se actualizan en la página de la `OnKillActive` (función).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]  
  
##  <a name="onquerycancel"></a>CPropertyPage::OnQueryCancel  
 Esta función miembro se llama el marco de trabajo cuando el usuario hace clic en el botón Cancelar y antes de cancelar la acción ha tenido lugar.  
  
```  
virtual BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **FALSE** para evitar la operación de cancelación o TRUE para permitirlo.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para especificar una acción realizada por el programa cuando el usuario hace clic en el botón Cancelar.  
  
 La implementación predeterminada de `OnQueryCancel` devuelve **TRUE**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]  
  
##  <a name="onreset"></a>CPropertyPage::OnReset  
 El marco de trabajo llama a esta función miembro cuando el usuario elige el botón Cancelar.  
  
```  
virtual void OnReset();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el marco de trabajo llama a esta función, se descartan los cambios a todas las páginas de propiedad realizados por el usuario anteriormente eligiendo el botón Aplicar ahora y la hoja de propiedades conserva el foco.  
  
 Reemplace esta función miembro para especificar la acción realizada por el programa cuando el usuario hace clic en el botón Cancelar.  
  
 La implementación predeterminada de `OnReset` no hace nada.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertyPage::OnCancel](#oncancel).  
  
##  <a name="onsetactive"></a>Notificaciones CPropertyPage:: OnSetActive  
 Esta función miembro se llama el marco de trabajo cuando la página elegida por el usuario y se convierte en la página activa.  
  
```  
virtual BOOL OnSetActive();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la página se estableció correctamente active; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para llevar a cabo tareas cuando se activa una página. La invalidación de esta función miembro normalmente llamaría a la versión predeterminada después de actualizar los miembros de datos, para permitir que se va a actualizar los controles de página con los nuevos datos.  
  
 La implementación predeterminada crea la ventana de la página, si no ha creado previamente y facilita la página activa.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).  
  
##  <a name="onwizardback"></a>CPropertyPage::OnWizardBack  
 El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón Atrás en un asistente.  
  
```  
virtual LRESULT OnWizardBack();
```  
  
### <a name="return-value"></a>Valor devuelto  
 0 para adelantar automáticamente a la página siguiente; -1 para evitar que se cambie la página. Para saltar a una página distinta a la siguiente, devolver el identificador del cuadro de diálogo que se mostrará.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para especificar alguna acción que el usuario debe adoptar cuando se presiona el botón Atrás.  
  
 Para obtener más información sobre cómo hacer que una hoja de propiedades de tipo asistente, consulte [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]  
  
##  <a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish  
 El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón Finalizar en un asistente.  
  
```  
virtual BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la hoja de propiedades se destruye cuando finalice el Asistente; cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un usuario hace clic en el **finalizar** botón de un asistente, el marco de trabajo llama a esta función; si `OnWizardFinish` devuelve **TRUE** (un valor distinto de cero), la hoja de propiedades es capaz de ser destruidos (pero no se destruye realmente). Llame a `DestroyWindow` para destruir la hoja de propiedades. No llame a `DestroyWindow` de `OnWizardFinish`; Esto hará que otros errores o daños en el montón.  
  
 Puede invalidar esta función miembro para especificar alguna acción que el usuario debe adoptar cuando se presiona el botón Finalizar. Cuando se reemplaza esta función, devuelva **FALSE** para impedir que la hoja de propiedades que se destruya.  
  
 Para obtener más información acerca de los mensajes de notificación se envía cuando el usuario presiona el botón Finalizar en una hoja de propiedades del asistente, consulte [PSN_WIZFINISH](http://msdn.microsoft.com/library/windows/desktop/bb774571) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre cómo hacer que una hoja de propiedades de tipo asistente, consulte [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]  
  
##  <a name="onwizardnext"></a>CPropertyPage::OnWizardNext  
 El marco de trabajo llama a esta función miembro cuando el usuario hace clic en el botón siguiente de un asistente.  
  
```  
virtual LRESULT OnWizardNext();
```  
  
### <a name="return-value"></a>Valor devuelto  
 0 para adelantar automáticamente a la página siguiente; -1 para evitar que se cambie la página. Para saltar a una página distinta a la siguiente, devolver el identificador del cuadro de diálogo que se mostrará.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para especificar alguna acción que el usuario debe adoptar cuando se presiona el botón siguiente.  
  
 Para obtener más información sobre cómo hacer que una hoja de propiedades de tipo asistente, consulte [CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView n.º 123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]  
  
##  <a name="querysiblings"></a>CPropertyPage::QuerySiblings  
 Llame a esta función miembro para reenviar un mensaje a cada página en la hoja de propiedades.  
  
```  
LRESULT QuerySiblings(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 `wParam`  
 Especifica información adicional de dependiente de mensaje.  
  
 `lParam`  
 Especifica información adicional de dependiente de mensaje  
  
### <a name="return-value"></a>Valor devuelto  
 El valor es distinto de cero de una página en la hoja de propiedades, o 0 si todas las páginas devuelven un valor de 0.  
  
### <a name="remarks"></a>Comentarios  
 Si una página devuelve un valor distinto de cero, la hoja de propiedades no envía el mensaje a las páginas siguientes.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView #124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]  
  
##  <a name="setmodified"></a>CPropertyPage:: SetModified  
 Llame a esta función miembro para habilitar o deshabilitar el botón Aplicar ahora, en función de si se debe aplicar la configuración en la página de propiedades para el objeto externo adecuado.  
  
```  
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bChanged`  
 **TRUE** para indicar que la configuración de la página de propiedades se han modificado desde la última vez que fueron aplicadas; **FALSE** para indicar que la configuración de la página de propiedades se han aplicado o debe omitirse.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo realiza seguimiento de los cuales páginas son "modificadas", es decir, páginas de propiedades para el que se llamó a **SetModified (TRUE)**. Siempre se habilitará el botón Aplicar ahora si se llama a **SetModified (TRUE)** para una de las páginas. Se deshabilitará el botón Aplicar ahora cuando se llama a **SetModified (FALSE)** para una de las páginas, pero solo si ninguna de las otras páginas es "sucias".  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView número 127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CMNCTRL1 de ejemplo MFC](../../visual-cpp-samples.md)   
 [CMNCTRL2 de ejemplo MFC](../../visual-cpp-samples.md)   
 [Ejemplo MFC PROPDLG](../../visual-cpp-samples.md)   
 [Ejemplo SNAPVW de MFC](../../visual-cpp-samples.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPropertySheet (clase)](../../mfc/reference/cpropertysheet-class.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)

