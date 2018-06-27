---
title: CDialogBar (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
dev_langs:
- C++
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5477921ff89c8bb0b23245d3848139a7c7c86444
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951561"
---
# <a name="cdialogbar-class"></a>CDialogBar (clase)
Proporciona la funcionalidad de un cuadro de diálogo no modal de Windows en una barra de controles.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDialogBar : public CControlBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDialogBar::CDialogBar](#cdialogbar)|Construye un objeto `CDialogBar`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDialogBar::Create](#create)|Crea una barra de cuadro de diálogo de Windows y lo adjunta a la `CDialogBar` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Una barra de cuadro de diálogo es similar a un cuadro de diálogo que contiene los controles estándar de Windows que el usuario puede cambiar mediante tabulación entre. Similitud otra es crear una plantilla de cuadro de diálogo para representar la barra de cuadro de diálogo.  
  
 Crear y usar una barra de cuadro de diálogo es similar a crear y usar un `CFormView` objeto. En primer lugar, use la [editor de cuadro de diálogo](../../windows/dialog-editor.md) para definir una plantilla de cuadro de diálogo con el estilo **WS_CHILD** y ningún otro estilo. La plantilla no debe tener el estilo **WS_VISIBLE**. En el código de aplicación, llame al constructor para construir el `CDialogBar` de objeto y después llamar a `Create` para crear la ventana de la barra de cuadro de diálogo y adjuntarla a la `CDialogBar` objeto.  
  
 Para obtener más información sobre `CDialogBar`, vea el artículo [barras de cuadro de diálogo](../../mfc/dialog-bars.md) y [Nota técnica 31](../../mfc/tn031-control-bars.md), barras de Control.  
  
> [!NOTE]
>  En la versión actual, un `CDialogBar` objeto no puede hospedar controles de formularios Windows Forms. Para obtener más información acerca de los controles de formularios Windows Forms en Visual C++, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="cdialogbar"></a>  CDialogBar::CDialogBar  
 Construye un objeto `CDialogBar`.  
  
```  
CDialogBar();
```  
  
##  <a name="create"></a>  CDialogBar::Create  
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
 *pParentWnd*  
 Un puntero al elemento primario `CWnd` objeto.  
  
 *lpszTemplateName*  
 Un puntero al nombre de la `CDialogBar` plantilla de recursos de cuadro de diálogo del objeto.  
  
 *nStyle*  
 El estilo de barra de herramientas. Estilos de barra de herramientas adicionales compatibles son:  
  
- **CBRS_TOP** barra de Control se encuentra en la parte superior de la ventana de marco.  
  
- **CBRS_BOTTOM** barra de Control se encuentra en la parte inferior de la ventana de marco.  
  
- **CBRS_NOALIGN** barra de Control no se cambia de posición cuando se cambia de tamaño el elemento primario.  
  
- **CBRS_TOOLTIPS** barra de Control muestra información sobre herramientas.  
  
- **CBRS_SIZE_DYNAMIC** barra de controles es dinámica.  
  
- **CBRS_SIZE_FIXED** barra de controles es fijo.  
  
- **CBRS_FLOATING** barra de Control está flotando.  
  
- **CBRS_FLYBY** barra de estado muestra información acerca del botón.  
  
- **CBRS_HIDE_INPLACE** barra de Control no se muestra al usuario.  
  
 *nID*  
 Id. de control de la barra de cuadro de diálogo.  
  
 *nIDTemplate*  
 El identificador de recurso de la `CDialogBar` de plantilla de cuadro de diálogo del objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si especifica la **CBRS_TOP** o **CBRS_BOTTOM** estilo de alineación es el ancho de la barra de cuadro de diálogo de la ventana de marco y su alto es que el recurso especificado por *nIDTemplate*. Si especifica la **CBRS_LEFT** o **CBRS_RIGHT** estilo de alineación es el alto de la barra de cuadro de diálogo de la ventana de marco y su ancho es que el recurso especificado por *nIDTemplate*.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC CTRLBARS](../../visual-cpp-samples.md)   
 [CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase CFormView](../../mfc/reference/cformview-class.md)   
 [CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)
