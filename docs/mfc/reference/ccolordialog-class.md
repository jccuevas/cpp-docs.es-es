---
title: Clase CColorDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
dev_langs: C++
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38fbca875847e557981c09dc418c8e0ef65bed6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccolordialog-class"></a>Clase CColorDialog
Le permite especificar un cuadro de diálogo de selección de color en la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CColorDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CColorDialog::CColorDialog](#ccolordialog)|Construye un objeto `CColorDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CColorDialog::DoModal](#domodal)|Muestra un cuadro de diálogo color y permite al usuario realizar una selección.|  
|[CColorDialog::GetColor](#getcolor)|Devuelve un **COLORREF** estructura que contiene los valores del color seleccionado.|  
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Recupera los colores personalizados creados por el usuario.|  
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Fuerza la selección de color actual en el color especificado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CColorDialog::OnColorOK](#oncolorok)|Reemplace este valor para validar el color especificado en el cuadro de diálogo.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CColorDialog::m_cc](#m_cc)|Una estructura usada para personalizar la configuración del cuadro de diálogo.|  
  
## <a name="remarks"></a>Comentarios  
 Un `CColorDialog` objeto es un cuadro de diálogo con una lista de colores que se definen para el sistema de presentación. El usuario puede seleccionar o crear un color determinado en la lista, que se indica a continuación volver a la aplicación cuando se cierra el cuadro de diálogo.  
  
 Para construir un `CColorDialog` de objeto, utilice el constructor proporcionado o derivar una clase nueva y usar su propio constructor personalizado.  
  
 Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar los valores de la [m_cc](#m_cc) estructura para inicializar los valores de los controles del cuadro de diálogo. El `m_cc` estructura es de tipo [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830).  
  
 Después de inicializar los controles del cuadro de diálogo, llame a la `DoModal` función de miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar un color. `DoModal`Devuelve la selección del usuario de uno de ellos Aceptar del cuadro de diálogo ( **IDOK**) o Cancelar ( **IDCANCEL**) botón.  
  
 Si `DoModal` devuelve **IDOK**, puede usar uno de `CColorDialog`de funciones de miembro para recuperar la información de entrada por el usuario.  
  
 Puede utilizar las ventanas [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) función para determinar si se produjo un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error.  
  
 `CColorDialog`se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3.1 y posteriores de Windows.  
  
 Para personalizar el cuadro de diálogo, derive una clase de `CColorDialog`, proporcione una plantilla de cuadro de diálogo personalizado y agregar un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes sin procesar se deben pasar a la clase base.  
  
 Personalizar la función de enlace no es necesario.  
  
> [!NOTE]
>  En algunas instalaciones de la `CColorDialog` objeto no se mostrará con un fondo gris si ha utilizado el marco de trabajo para hacer otras `CDialog` gris de objetos.  
  
 Para obtener más información sobre el uso de `CColorDialog`, consulte [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CColorDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdlgs.h  
  
##  <a name="ccolordialog"></a>CColorDialog::CColorDialog  
 Construye un objeto `CColorDialog`.  
  
```  
CColorDialog(
    COLORREF clrInit = 0,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *clrInit*  
 La selección de color predeterminado. Si no se especifica ningún valor, el valor predeterminado es RGB(0,0,0) (negro).  
  
 `dwFlags`  
 Un conjunto de marcas que personalizan la función y la apariencia del cuadro de diálogo. Para obtener más información, consulte el [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830) estructura en el SDK de Windows.  
  
 `pParentWnd`  
 Un puntero a la ventana primaria o propietaria del cuadro de diálogo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]  
  
##  <a name="domodal"></a>CColorDialog::DoModal  
 Llame a esta función para mostrar el cuadro de diálogo color común de Windows y permitir al usuario seleccionar un color.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 **IDOK** o **IDCANCEL**. Si **IDCANCEL** es devuelto, llame a las ventanas [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) función para determinar si se produjo un error.  
  
 **IDOK** y **IDCANCEL** son constantes que indican si el usuario selecciona el botón Aceptar o en Cancelar.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar las distintas opciones del cuadro de diálogo color estableciendo los miembros de la [m_cc](#m_cc) estructura, debe hacerlo antes de llamar a `DoModal` , pero una vez construido el objeto de cuadro de diálogo.  
  
 Después de llamar a `DoModal`, se puede llamar a otra funciones miembro para recuperar la configuración o la entrada de información por el usuario en el cuadro de diálogo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CColorDialog::CColorDialog](#ccolordialog).  
  
##  <a name="getcolor"></a>CColorDialog::GetColor  
 Llame a esta función después de llamar a `DoModal` para recuperar la información sobre el color seleccionado por el usuario.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que contiene la información de RGB del color seleccionado en el cuadro de diálogo color.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]  
  
##  <a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors  
 `CColorDialog`objetos permiten al usuario, además de elegir los colores, para definir un máximo de 16 colores personalizados.  
  
```  
static COLORREF* PASCAL GetSavedCustomColors();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una matriz de 16 valores de color RGB que almacena los colores personalizados creados por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 El `GetSavedCustomColors` función miembro proporciona acceso a estos colores. Estos colores se pueden recuperar tras [DoModal](#domodal) devuelve **IDOK**.  
  
 Cada uno de los 16 valores RGB en la matriz devuelta se inicializa en RGB(255,255,255) (blanco). Los colores personalizados elegidos por el usuario se guardan solo entre las invocaciones de cuadro de diálogo dentro de la aplicación. Si desea guardar estos colores entre las distintas invocaciones de la aplicación, debe guárdelas en alguna otra manera, como en una inicialización (. Archivo INI).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]  
  
##  <a name="m_cc"></a>CColorDialog::m_cc  
 Una estructura de tipo [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830), cuyos miembros almacenan las características y los valores del cuadro de diálogo.  
  
```  
CHOOSECOLOR m_cc;  
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear un `CColorDialog` objeto, puede usar `m_cc` para establecer varios aspectos del cuadro de diálogo antes de llamar a la [DoModal](#domodal) función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]  
  
##  <a name="oncolorok"></a>CColorDialog::OnColorOK  
 Reemplace este valor para validar el color especificado en el cuadro de diálogo.  
  
```  
virtual BOOL OnColorOK();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no se debe descartar el cuadro de diálogo; en caso contrario 0 para aceptar el color que se escribió.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función sólo si desea proporcionar validación personalizada del color que el usuario selecciona en el cuadro de diálogo color.  
  
 El usuario puede seleccionar un color mediante uno de los dos métodos siguientes:  
  
-   Al hacer clic en un color en la paleta de colores. Los valores RGB del color seleccionado, a continuación, se reflejan en los cuadros de edición RGB correspondientes.  
  
-   Cuadros de edición de introducir valores en el RGB  
  
 Reemplazar `OnColorOK` permite rechazar un color que el usuario escribe en un cuadro de diálogo común de color por alguna razón específica de la aplicación.  
  
 Normalmente, no es necesario usar esta función porque el marco de trabajo proporciona una validación predeterminada de colores y muestra un cuadro de mensaje si no se especifica un color no válido.  
  
 Puede llamar a [SetCurrentColor](#setcurrentcolor) desde `OnColorOK` para forzar una selección de color. Una vez `OnColorOK` se ha desencadenado (es decir, el usuario hace clic en **Aceptar** para aceptar el cambio de color), puede llamar a [GetColor](#getcolor) para obtener el valor RGB del color nuevo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]  
  
##  <a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor  
 Llame a esta función después de llamar a `DoModal` para forzar la selección de color actual en el valor de color especificado en `clr`.  
  
```  
void SetCurrentColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parámetros  
 `clr`  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se llama desde dentro de un controlador de mensajes o `OnColorOK`. El cuadro de diálogo actualizará automáticamente la selección del usuario en función del valor de la `clr` parámetro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CColorDialog::OnColorOK](#oncolorok).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [Ejemplo MFC DRAWCLI](../../visual-cpp-samples.md)   
 [Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

