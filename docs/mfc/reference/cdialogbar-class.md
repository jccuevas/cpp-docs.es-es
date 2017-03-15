---
title: CDialogBar (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialogBar
dev_langs:
- C++
helpviewer_keywords:
- dialog bars, Windows modeless dialog box
- CDialogBar class
- dialog boxes, modeless
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
caps.latest.revision: 23
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
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 33dc5f5f4d345745a4b9435e725f411f4387e287
ms.lasthandoff: 02/24/2017

---
# <a name="cdialogbar-class"></a>CDialogBar (clase)
Proporciona la funcionalidad de un cuadro de diálogo no modal de Windows en una barra de controles.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDialogBar : public CControlBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDialogBar::CDialogBar](#cdialogbar)|Construye un objeto `CDialogBar`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDialogBar::Create](#create)|Crea una barra de cuadro de diálogo de Windows y lo adjunta a la `CDialogBar` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Una barra de cuadro de diálogo es similar a un cuadro de diálogo que contiene los controles estándar de Windows que el usuario puede cambiar entre. Similitud otra es crear una plantilla de cuadro de diálogo para representar la barra de cuadro de diálogo.  
  
 Crear y usar una barra de cuadro de diálogo es similar a crear y usar un `CFormView` objeto. En primer lugar, utilice la [editor de cuadro de diálogo](../../windows/dialog-editor.md) para definir una plantilla de cuadro de diálogo con el estilo **WS_CHILD** y ningún otro estilo. La plantilla no debe tener el estilo **WS_VISIBLE**. En el código de aplicación, llame al constructor para construir la `CDialogBar` objeto, a continuación, llame a **crear** para crear la ventana de la barra de cuadro de diálogo y adjuntarlo a la `CDialogBar` objeto.  
  
 Para obtener más información sobre `CDialogBar`, vea el artículo [barras de cuadro de diálogo](../../mfc/dialog-bars.md) y [Nota técnica 31](../../mfc/tn031-control-bars.md), barras de Control.  
  
> [!NOTE]
>  En la versión actual, un `CDialogBar` objeto no puede hospedar controles de formularios Windows Forms. Para obtener más información acerca de los controles de formularios Windows Forms en Visual C++, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="a-namecdialogbara--cdialogbarcdialogbar"></a><a name="cdialogbar"></a>CDialogBar::CDialogBar  
 Construye un objeto `CDialogBar`.  
  
```  
CDialogBar();
```  
  
##  <a name="a-namecreatea--cdialogbarcreate"></a><a name="create"></a>CDialogBar::Create  
 Carga la plantilla de recursos de cuadro de diálogo especificada por `lpszTemplateName` o `nIDTemplate`, crea la ventana de la barra de cuadro de diálogo, Establece el estilo y lo asocia a la `CDialogBar` objeto.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID);

 
virtual BOOL Create(
    CWnd* pParentWnd,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Un puntero al elemento primario `CWnd` objeto.  
  
 `lpszTemplateName`  
 Un puntero al nombre de la `CDialogBar` plantilla de recursos de cuadro de diálogo del objeto.  
  
 `nStyle`  
 El estilo de barra de herramientas. Estilos de barra de herramientas adicionales compatibles son:  
  
- `CBRS_TOP`Barra de control está en la parte superior de la ventana de marco.  
  
- `CBRS_BOTTOM`Barra de control está en la parte inferior de la ventana de marco.  
  
- `CBRS_NOALIGN`Barra de control no se cambia de posición cuando se cambia el elemento primario.  
  
- `CBRS_TOOLTIPS`Barra de control muestra información sobre herramientas.  
  
- **CBRS_SIZE_DYNAMIC** barra de controles es dinámica.  
  
- **CBRS_SIZE_FIXED** barra de controles es fijo.  
  
- **CBRS_FLOATING** barra de controles está flotando.  
  
- `CBRS_FLYBY`Barra de estado muestra información acerca del botón.  
  
- **CBRS_HIDE_INPLACE** no se muestra la barra de Control al usuario.  
  
 `nID`  
 El identificador del control de la barra de cuadro de diálogo.  
  
 `nIDTemplate`  
 El identificador de recurso de la `CDialogBar` de plantilla de cuadro de diálogo del objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si especifica la `CBRS_TOP` o `CBRS_BOTTOM` estilo de alineación es el ancho de la barra de cuadro de diálogo de la ventana de marco y su alto es que el recurso especificado por `nIDTemplate`. Si especifica la `CBRS_LEFT` o `CBRS_RIGHT` estilo de alineación es el alto de la barra de cuadro de diálogo de la ventana de marco y su ancho es que el recurso especificado por `nIDTemplate`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCMessageMaps&#13;](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CTRLBARS de ejemplo de MFC](../../visual-cpp-samples.md)   
 [CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CFormView](../../mfc/reference/cformview-class.md)   
 [CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)

