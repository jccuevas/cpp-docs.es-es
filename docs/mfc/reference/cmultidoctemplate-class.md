---
title: Clase CMultiDocTemplate | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- MDI, template
- CMultiDocTemplate class
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
caps.latest.revision: 21
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
ms.openlocfilehash: 6e58325cd4dcaec01bf8a76006bb397fccd9a171
ms.lasthandoff: 02/24/2017

---
# <a name="cmultidoctemplate-class"></a>Clase CMultiDocTemplate
Define una plantilla de documento que implementa la interfaz de múltiples documentos (MDI).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMultiDocTemplate : public CDocTemplate  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|Construye un objeto `CMultiDocTemplate`.|  
  
## <a name="remarks"></a>Comentarios  
 Una aplicación MDI utiliza la ventana de marco principal como un área de trabajo en el que el usuario puede abrir ventanas de marco de documento de cero o más, cada uno de los cuales muestra un documento. Para obtener una descripción más detallada de la MDI, consulte *instrucciones de la interfaz de Windows para el diseño de Software de*.  
  
 Una plantilla de documento define las relaciones entre los tres tipos de clases:  
  
-   Una clase de documento, que derivan de [CDocument](../../mfc/reference/cdocument-class.md).  
  
-   Una clase de vista, que muestra los datos de la clase de documento mencionado anteriormente. Puede derivar de esta clase desde [CView](../../mfc/reference/cview-class.md), `CScrollView`, `CFormView`, o `CEditView`. (También puede utilizar `CEditView` directamente.)  
  
-   Una clase de ventana de marco, que contiene la vista. Puede derivar esta clase a partir de una plantilla de documento MDI, `CMDIChildWnd`, o bien, si no es necesario personalizar el comportamiento de las ventanas de marco de documento, puede usar [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) directamente sin tener que derivar su propia clase.  
  
 Una aplicación MDI puede admitir más de un tipo de documento y documentos de diferentes tipos pueden estar abiertos al mismo tiempo. La aplicación tiene una plantilla de documento para cada tipo de documento que admite. Por ejemplo, si su aplicación MDI admite hojas de cálculo y documentos de texto, la aplicación tiene dos `CMultiDocTemplate` objetos.  
  
 La aplicación utiliza las plantillas de documento, cuando el usuario crea un nuevo documento. Si la aplicación admite más de un tipo de documento, el marco de trabajo obtiene los nombres de los tipos de documentos admitidos en las plantillas de documento y los muestra en una lista en el cuadro de diálogo nuevo archivo. Una vez que el usuario ha seleccionado un tipo de documento, la aplicación crea un objeto de clase de documento, un objeto de ventana de marco y un objeto de vista y los conecta entre sí.  
  
 No es necesario llamar a funciones de cualquier miembro `CMultiDocTemplate` excepto el constructor. Los identificadores de framework `CMultiDocTemplate` objetos internamente.  
  
 Para obtener más información sobre `CMultiDocTemplate`, consulte [plantillas de documento y el proceso de creación de documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CMultiDocTemplate`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cmultidoctemplate"></a>CMultiDocTemplate::CMultiDocTemplate  
 Construye un objeto `CMultiDocTemplate`.  
  
```  
CMultiDocTemplate(
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
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 Tenga en cuenta que la cadena comienza con un carácter '\n'; Esto es porque la primera subcadena no se utiliza para aplicaciones MDI y por lo tanto, no se incluye. Puede editar esta cadena mediante el editor de cadenas; toda la cadena aparece como una sola entrada en el Editor de cadenas, no como siete entradas independientes.  
  
 Para obtener más información acerca de estos tipos de recursos, consulte [editores de recursos](../../windows/resource-editors.md).  
  
 `pDocClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de documento. Esta clase es un **CDocument**-definir para representar los documentos de clase derivada.  
  
 `pFrameClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de ventana de marco. Esta clase puede ser un `CMDIChildWnd`-clase derivada, o puede ser `CMDIChildWnd` si desea el comportamiento predeterminado para las ventanas de marco de documento.  
  
 `pViewClass`  
 Apunta a la `CRuntimeClass` objeto de la clase de vista. Esta clase es un `CView`-se definen para mostrar los documentos de clase derivada.  
  
### <a name="remarks"></a>Comentarios  
 Asignar dinámicamente uno `CMultiDocTemplate` objeto para cada tipo de documento que su aplicación admita y pasar cada uno de ellos a `CWinApp::AddDocTemplate` desde el `InitInstance` función miembro de la clase de aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#92;](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]  
  
 Este es un ejemplo de segundo.  
  
 [!code-cpp[NVC_MFCDocView&#93;](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [Clase CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp (clase)](../../mfc/reference/cwinapp-class.md)

