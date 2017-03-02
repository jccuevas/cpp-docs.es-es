---
title: Clase CSingleDocTemplate | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSingleDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- templates, SDI
- document templates, single
- single document interface (SDI), applications
- CSingleDocTemplate class
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
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
ms.openlocfilehash: 78e288dd958e73495a8d513d7fe3427ccc956a61
ms.lasthandoff: 02/24/2017

---
# <a name="csingledoctemplate-class"></a>Clase CSingleDocTemplate
Define una plantilla de documento que implementa la interfaz de un único documento (SDI).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSingleDocTemplate : public CDocTemplate  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|Construye un objeto `CSingleDocTemplate`.|  
  
## <a name="remarks"></a>Comentarios  
 Una aplicación SDI utiliza la ventana de marco principal para mostrar un documento; solo se puede abrir un documento a la vez.  
  
 Una plantilla de documento define la relación entre los tres tipos de clases:  
  
-   Una clase de documento, que derivan de **CDocument**.  
  
-   Una clase de vista, que muestra los datos de la clase de documento mencionado anteriormente. Puede derivar de esta clase desde `CView`, `CScrollView`, `CFormView`, o `CEditView`. (También puede utilizar `CEditView` directamente.)  
  
-   Una clase de ventana de marco, que contiene la vista. Puede derivar esta clase a partir de una plantilla de documento SDI, `CFrameWnd`; si no es necesario personalizar el comportamiento de los principales de la ventana de marco, puede usar `CFrameWnd` directamente sin tener que derivar su propia clase.  
  
 Normalmente, una aplicación SDI admite un tipo de documento, por lo que sólo tiene un `CSingleDocTemplate` objeto. Solo se puede abrir un documento a la vez.  
  
 No es necesario llamar a funciones de cualquier miembro `CSingleDocTemplate` excepto el constructor. Los identificadores de framework `CSingleDocTemplate` objetos internamente.  
  
 Para obtener más información sobre el uso de `CSingleDocTemplate`, consulte [plantillas de documento y el proceso de creación de documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CSingleDocTemplate`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-namecsingledoctemplatea--csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a>CSingleDocTemplate::CSingleDocTemplate  
 Construye un objeto `CSingleDocTemplate`.  
  
```  
CSingleDocTemplate(
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDResource`  
 Especifica el identificador de los recursos utilizados con el tipo de documento. Esto puede incluir menú, icono, tabla de aceleradores y los recursos de cadena.  
  
 El recurso de cadena que consta de hasta siete subcadenas separados por el carácter '\n' (es necesario el carácter '\n' como marcador de posición si no se incluye una subcadena; sin embargo, no son necesarios los caracteres '\n'); Estos subcadenas describen el tipo de documento. Para obtener información sobre las subcadenas, consulte [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Este recurso de cadena se encuentra en el archivo de recursos de la aplicación. Por ejemplo:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"`  
  
 `END`  
  
 Puede editar esta cadena mediante el editor de cadenas; toda la cadena aparece como una sola entrada en el Editor de cadenas, no como siete entradas independientes.  
  
 Para obtener más información acerca de estos tipos de recursos, consulte el [Editor de cadenas](../../windows/string-editor.md).  
  
 `pDocClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de documento. Esta clase es un **CDocument**-definir para representar los documentos de clase derivada.  
  
 `pFrameClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de ventana de marco. Esta clase puede ser un `CFrameWnd`-clase derivada, o puede ser `CFrameWnd` si desea el comportamiento predeterminado de la ventana de marco principal.  
  
 `pViewClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de vista. Esta clase es un `CView`-se definen para mostrar los documentos de clase derivada.  
  
### <a name="remarks"></a>Comentarios  
 Asignar dinámicamente un `CSingleDocTemplate` objeto y pasarlo al `CWinApp::AddDocTemplate` desde el `InitInstance` función miembro de la clase de aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocViewSDI&#13;](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocViewSDI&#14;](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC DOCKTOOL](../../visual-cpp-samples.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument (clase)](../../mfc/reference/cdocument-class.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Clase CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CWinApp (clase)](../../mfc/reference/cwinapp-class.md)

