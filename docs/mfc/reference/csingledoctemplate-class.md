---
title: Clase CSingleDocTemplate | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
dev_langs: C++
helpviewer_keywords: CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e23db022f62dab171359f2d0a9cdb158c36557c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
 Una aplicación SDI utiliza la ventana de marco principal para mostrar un documento; sólo se puede abrir un documento a la vez.  
  
 Una plantilla de documento define la relación entre los tres tipos de clases:  
  
-   Una clase de documento, que derivan de **CDocument**.  
  
-   Una clase de vista, que muestra los datos de la clase de documento mencionado anteriormente. Puede derivar de esta clase desde `CView`, `CScrollView`, `CFormView`, o `CEditView`. (También puede usar `CEditView` directamente.)  
  
-   Una clase de ventana de marco, que contiene la vista. Puede derivar esta clase a partir de una plantilla de documento SDI, `CFrameWnd`; si no es necesario personalizar el comportamiento de los principales las ventanas de marco, puede usar `CFrameWnd` directamente sin tener que derivar su propia clase.  
  
 Por lo general, una aplicación SDI admite un tipo de documento, por lo que sólo tiene un `CSingleDocTemplate` objeto. Sólo se puede abrir un documento a la vez.  
  
 No es necesario llamar a funciones de cualquier miembro `CSingleDocTemplate` excepto el constructor. Los identificadores de framework `CSingleDocTemplate` objetos internamente.  
  
 Para obtener más información sobre el uso de `CSingleDocTemplate`, consulte [plantillas de documento y el proceso de creación de documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CSingleDocTemplate`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="csingledoctemplate"></a>CSingleDocTemplate::CSingleDocTemplate  
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
 Especifica el identificador de los recursos utilizados con el tipo de documento. Esto puede incluir menú, icono, tabla de aceleradores y recursos de cadena.  
  
 El recurso de cadena consta de hasta siete subcadenas separados por el carácter '\n' (se necesita el carácter '\n' como marcador de posición si no se incluye una subcadena; sin embargo, no son necesarios los caracteres finales '\n'); Estos subcadenas describen el tipo de documento. Para obtener información sobre las subcadenas, consulte [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Este recurso de cadena se encuentra en el archivo de recursos de la aplicación. Por ejemplo:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"`  
  
 `END`  
  
 Puede editar esta cadena mediante el editor de cadenas; toda la cadena aparece como una sola entrada en el Editor de cadena, no como siete separe las entradas.  
  
 Para obtener más información acerca de estos tipos de recursos, consulte el [Editor de cadena](../../windows/string-editor.md).  
  
 `pDocClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de documento. Esta clase es un **CDocument**-deriva la clase que defina para representar los documentos.  
  
 `pFrameClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de ventana de marco. Esta clase puede ser un `CFrameWnd`-clase derivada, o puede ser `CFrameWnd` si desea el comportamiento predeterminado de la ventana de marco principal.  
  
 `pViewClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de vista. Esta clase es un `CView`-deriva la clase que defina para mostrar los documentos.  
  
### <a name="remarks"></a>Comentarios  
 Asignar dinámicamente un `CSingleDocTemplate` objeto y pasarlo a `CWinApp::AddDocTemplate` desde el `InitInstance` función miembro de la clase de aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC DOCKTOOL](../../visual-cpp-samples.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument (clase)](../../mfc/reference/cdocument-class.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Clase CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CWinApp (clase)](../../mfc/reference/cwinapp-class.md)
