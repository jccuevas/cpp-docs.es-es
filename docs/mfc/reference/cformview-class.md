---
title: Clase CFormView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFormView
dev_langs:
- C++
helpviewer_keywords:
- views, containing controls
- CFormView class
- form views
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 82b38b04aa3cf2368d41ee20847c952c3082d4e4
ms.lasthandoff: 02/24/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Se usa para la sincronización durante la inicialización.|  
  
## <a name="remarks"></a>Comentarios  
 Una vista de formulario es esencialmente una vista que contiene controles que se disponen en función de un recurso de plantilla de cuadro de diálogo. Use `CFormView` si quiere usar formularios en la aplicación. Estas vistas admiten el desplazamiento, según sea necesario mediante la [CScrollView](../../mfc/reference/cscrollview-class.md) funcionalidad.  
  
 Cuando esté [crear una aplicación basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md), su clase de vista se puede basar en `CFormView`, lo que una aplicación basada en formularios.  
  
 También puede insertar nuevos [formulario temas](../../mfc/form-views-mfc.md) en aplicaciones basadas en la vista de documento. Aunque la aplicación no admitía formularios inicialmente, Visual C++ agregará automáticamente esta compatibilidad al insertar un formulario nuevo.  
  
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
  
##  <a name="a-namecformviewa--cformviewcformview"></a><a name="cformview"></a>CFormView::CFormView  
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
 Cuando se crea un objeto de un tipo derivado de `CFormView`, invocará a uno de los constructores para crear el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista. Puede identificar el recurso por su nombre (pase una cadena como argumento al constructor) o por su identificador (pasar un entero sin signo como argumento).  
  
 La vista de formulario ventana y los controles secundarios no se crean hasta que `CWnd::Create` se llama. `CWnd::Create`es llamado por el marco como parte del proceso de creación documento y vista, que se controla mediante la plantilla de documento.  
  
> [!NOTE]
>  La clase derivada *debe* proporcionar su propio constructor. En el constructor, invocar el constructor, `CFormView::CFormView`, con el identificador como argumento tal como se muestra en la información general de clase anterior o el nombre del recurso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#90;](../../mfc/codesnippet/cpp/cformview-class_1.h)]  
  
 [!code-cpp[NVC_MFCDocView&#91;](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]  
  
##  <a name="a-nameisinitdlgcompleteda--cformviewisinitdlgcompleted"></a><a name="isinitdlgcompleted"></a>CFormView::IsInitDlgCompleted  
 Usado por MFC para garantizar que la inicialización se complete antes de llevar a cabo otras operaciones.  
  
```  
BOOL IsInitDlgCompleted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 True si se ha completado la función de inicialización para este cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC SNAPVW](../../visual-cpp-samples.md)   
 [Ejemplo de MFC VIEWEX](../../visual-cpp-samples.md)   
 [CScrollView (clase)](../../mfc/reference/cscrollview-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)   
 [CScrollView (clase)](../../mfc/reference/cscrollview-class.md)

