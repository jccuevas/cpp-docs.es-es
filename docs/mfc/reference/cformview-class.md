---
title: Clase CFormView | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
dev_langs:
- C++
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3486285b7b6430e9cd6f0e4a936aa3341bd72e0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cformview-class"></a>Clase CFormView
La clase base utilizada para las vistas de formulario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFormView : public CScrollView  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFormView::CFormView](#cformview)|Construye un objeto `CFormView`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Se usa para la sincronización durante la inicialización.|  
  
## <a name="remarks"></a>Comentarios  
 Una vista de formulario es esencialmente una vista que contiene controles que se disponen en función de un recurso de plantilla de cuadro de diálogo. Use `CFormView` si quiere usar formularios en la aplicación. Estas vistas admiten el desplazamiento, según sea necesario, con el [CScrollView](../../mfc/reference/cscrollview-class.md) funcionalidad.  
  
 Cuando esté [crear una aplicación basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md), puede basar su clase de vista en `CFormView`, lo que una aplicación basada en formularios.  
  
 También puede insertar nuevos [temas de formulario](../../mfc/form-views-mfc.md) en aplicaciones basadas en la vista de documento. Aunque la aplicación no admitía formularios inicialmente, Visual C++ agregará automáticamente esta compatibilidad al insertar un formulario nuevo.  
  
 El Asistente para aplicaciones MFC y el comando Agregar clase son los métodos preferidos para crear aplicaciones basadas en formularios. Si necesita crear una aplicación basada en formularios sin usar estos métodos, consulte [crear una aplicación basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 `CFormView`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="cformview"></a>  CFormView::CFormView  
 Construye un objeto `CFormView`.  
  
```  
CFormView(LPCTSTR lpszTemplateName);  
CFormView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTemplateName`  
 Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.  
  
 `nIDTemplate`  
 Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea un objeto de un tipo derivado de `CFormView`, invocar uno de los constructores para crear el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista. Puede identificar el recurso por su nombre (pasa una cadena como argumento al constructor) o por su identificador (pase un entero sin signo como argumento).  
  
 Los controles de ventana y secundario de la vista de formulario no se crean hasta que `CWnd::Create` se llama. `CWnd::Create` se llama el marco de trabajo como parte del proceso de creación documento y vista, que se controla mediante la plantilla de documento.  
  
> [!NOTE]
>  La clase derivada *debe* proporcionar su propio constructor. En el constructor, invocar el constructor, `CFormView::CFormView`, con el nombre del recurso o el identificador como un argumento tal como se muestra en la anterior información de clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]  
  
 [!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]  
  
##  <a name="isinitdlgcompleted"></a>  CFormView::IsInitDlgCompleted  
 Usado por MFC para garantizar que la inicialización se complete antes de llevar a cabo otras operaciones.  
  
```  
BOOL IsInitDlgCompleted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 True si se ha completado la función de inicialización para este cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo SNAPVW de MFC](../../visual-cpp-samples.md)   
 [Ejemplo VIEWEX de MFC](../../visual-cpp-samples.md)   
 [CScrollView (clase)](../../mfc/reference/cscrollview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)   
 [CScrollView (clase)](../../mfc/reference/cscrollview-class.md)
