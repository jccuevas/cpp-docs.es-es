---
title: CMultiDocTemplate (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 01988097d2b05daa6fc056c16f34ec00b45d6893
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071788"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate (clase)
Define una plantilla de documento que implementa la interfaz de múltiples documentos (MDI).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMultiDocTemplate : public CDocTemplate  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|Construye un objeto `CMultiDocTemplate`.|  
  
## <a name="remarks"></a>Comentarios  
 Una aplicación MDI utiliza la ventana de marco principal como un área de trabajo en el que el usuario puede abrir ventanas de marco de documento de cero o más, cada uno de los cuales muestra un documento. Para obtener una descripción más detallada de la MDI, consulte *directrices de interfaz de Windows para el diseño de Software*.  
  
 Una plantilla de documento define las relaciones entre los tres tipos de clases:  
  
-   Una clase de documento, que deriva de [CDocument](../../mfc/reference/cdocument-class.md).  
  
-   Una clase de vista, que muestra los datos de la clase de documento mencionada anteriormente. Puede derivar esta clase desde [CView](../../mfc/reference/cview-class.md), `CScrollView`, `CFormView`, o `CEditView`. (También puede usar `CEditView` directamente.)  
  
-   Una clase de ventana de marco, que contiene la vista. Puede derivar esta clase a partir de una plantilla de documento MDI, `CMDIChildWnd`, o bien, si no tiene que personalizar el comportamiento de las ventanas de marco de documento, puede usar [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) directamente sin tener que derivar su propia clase.  
  
 Una aplicación MDI puede admitir más de un tipo de documento y documentos de diferentes tipos pueden estar abiertos al mismo tiempo. La aplicación tiene una plantilla de documento para cada tipo de documento que admite. Por ejemplo, si su aplicación MDI es compatible con hojas de cálculo y documentos de texto, la aplicación tiene dos `CMultiDocTemplate` objetos.  
  
 La aplicación utiliza las plantillas de documento, cuando el usuario crea un nuevo documento. Si la aplicación admite más de un tipo de documento, a continuación, el marco de trabajo obtiene los nombres de los tipos de documento compatibles desde las plantillas de documento y los muestra en una lista en el cuadro de diálogo nuevo archivo. Una vez que el usuario ha seleccionado un tipo de documento, la aplicación crea un objeto de clase de documento, un objeto de ventana de marco y un objeto de vista y los asocia entre sí.  
  
 No es necesario llamar a funciones de cualquier miembro `CMultiDocTemplate` excepto el constructor. Los identificadores de framework `CMultiDocTemplate` objetos internamente.  
  
 Para obtener más información sobre `CMultiDocTemplate`, consulte [plantillas de documento y el proceso de creación de documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CMultiDocTemplate`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cmultidoctemplate"></a>  CMultiDocTemplate::CMultiDocTemplate  
 Construye un objeto `CMultiDocTemplate`.  
  
```  
CMultiDocTemplate(
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIDResource*  
 Especifica el identificador de los recursos utilizados con el tipo de documento. Esto puede incluir recursos de cadena, icono, tabla de aceleradores y menús.  
  
 El recurso de cadena consta de hasta siete subcadenas separadas por el carácter '\n' (el carácter '\n' es necesario como un marcador de posición si no se incluye una subcadena; sin embargo, no son necesarios los caracteres finales '\n'); Estos subcadenas describen el tipo de documento. Para obtener información sobre las subcadenas, consulte [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Este recurso de cadena se encuentra en el archivo de recursos de la aplicación. Por ejemplo:  
  
```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```
  
 Tenga en cuenta que la cadena comienza con un carácter '\n'; Esto es porque la primera subcadena no se utiliza para las aplicaciones MDI y por lo tanto, no se incluye. Puede editar esta cadena utilizando el editor de cadenas; toda la cadena aparece como una sola entrada en el Editor de cadena, no como siete entradas independientes.  
  
 Para obtener más información acerca de estos tipos de recursos, consulte [editores de recursos](../../windows/resource-editors.md).  
  
 *pDocClass*  
 Apunta a la `CRuntimeClass` objeto de la clase de documento. Esta clase es un `CDocument`-derivado de la clase que defina para representar los documentos.  
  
 *pFrameClass*  
 Apunta a la `CRuntimeClass` objeto de la clase de ventana de marco. Esta clase puede ser un `CMDIChildWnd`-clase derivada, o puede ser `CMDIChildWnd` Sí si desea el comportamiento predeterminado para las ventanas de marco de documento.  
  
 *pViewClass*  
 Apunta a la `CRuntimeClass` objeto de la clase de vista. Esta clase es un `CView`-derivado de la clase que defina para mostrar los documentos.  
  
### <a name="remarks"></a>Comentarios  
 Asignar dinámicamente uno `CMultiDocTemplate` objeto para cada tipo de documento que la aplicación admite y pasar cada uno de ellos a `CWinApp::AddDocTemplate` desde el `InitInstance` función miembro de la clase de aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]  
  
 Este es un ejemplo de segundo.  
  
 [!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [CSingleDocTemplate (clase)](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp (clase)](../../mfc/reference/cwinapp-class.md)
