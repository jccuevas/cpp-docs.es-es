---
title: CMultiDocTemplate (clase)
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: 3b3f239b05b1cf7661929333e2d616acce6bedb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319741"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate (clase)

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

## <a name="remarks"></a>Observaciones

Una aplicación MDI utiliza la ventana de marco principal como un espacio de trabajo en el que el usuario puede abrir cero o más ventanas de marco de documento, cada una de las cuales muestra un documento. Para obtener una descripción más detallada del MDI, consulte Directrices de *la interfaz*de Windows para el diseño de software .

Una plantilla de documento define las relaciones entre tres tipos de clases:

- Una clase de documento, que se deriva de [CDocument](../../mfc/reference/cdocument-class.md).

- Una clase de vista, que muestra los datos de la clase de documento enumerada anteriormente. Puede derivar esta clase de `CScrollView` `CFormView` [CView](../../mfc/reference/cview-class.md), , , o `CEditView`. (También puede `CEditView` utilizar directamente.)

- Una clase de ventana de marco, que contiene la vista. Para una plantilla de documento MDI, `CMDIChildWnd`puede derivar esta clase de , o, si no necesita personalizar el comportamiento de las ventanas de marco de documento, puede usar [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) directamente sin derivar su propia clase.

Una aplicación MDI puede admitir más de un tipo de documento y los documentos de diferentes tipos pueden estar abiertos al mismo tiempo. La aplicación tiene una plantilla de documento para cada tipo de documento que admite. Por ejemplo, si la aplicación MDI admite hojas de `CMultiDocTemplate` cálculo y documentos de texto, la aplicación tiene dos objetos.

La aplicación utiliza las plantillas de documento cuando el usuario crea un nuevo documento. Si la aplicación admite más de un tipo de documento, el marco de trabajo obtiene los nombres de los tipos de documento admitidos de las plantillas de documento y los muestra en una lista en el cuadro de diálogo Nuevo archivo. Una vez que el usuario ha seleccionado un tipo de documento, la aplicación crea un objeto de clase de documento, un objeto de ventana de marco y un objeto de vista y los adjunta entre sí.

No es necesario llamar a `CMultiDocTemplate` ninguna función miembro de excepto el constructor. El marco `CMultiDocTemplate` de trabajo controla los objetos internamente.

Para obtener `CMultiDocTemplate`más información sobre , consulte Plantillas de documento y Proceso de creación de [documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a>CMultiDocTemplate::CMultiDocTemplate

Construye un objeto `CMultiDocTemplate`.

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parámetros

*nIDResource*<br/>
Especifica el identificador de los recursos utilizados con el tipo de documento. Esto puede incluir menú, icono, tabla de aceleradores y recursos de cadena.

El recurso de cadena consta de hasta siete subcadenas separadas por el carácter ''n' (se necesita el carácter ''n' como un titular de posición si no se incluye una subcadena; sin embargo, no es necesario dejar de caracteres 'n'); estas subcadenas describen el tipo de documento. Para obtener información sobre las subcadenas, vea [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Este recurso de cadena se encuentra en el archivo de recursos de la aplicación. Por ejemplo:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Tenga en cuenta que la cadena comienza con un carácter 'n'; esto se debe a que la primera subcadena no se utiliza para aplicaciones MDI, por lo que no se incluye. Puede editar esta cadena mediante el editor de cadenas; toda la cadena aparece como una sola entrada en el Editor de cadenas, no como siete entradas independientes.

Para obtener más información acerca de estos tipos de recursos, vea [Editores de](../../windows/resource-editors.md)recursos .

*pDocClass*<br/>
Apunta al `CRuntimeClass` objeto de la clase de documento. Esta clase `CDocument`es una clase derivada que se define para representar los documentos.

*pFrameClass*<br/>
Apunta al `CRuntimeClass` objeto de la clase frame-window. Esta clase puede `CMDIChildWnd`ser una clase derivada, `CMDIChildWnd` o puede ser en sí misma si desea un comportamiento predeterminado para las ventanas de marco de documento.

*pViewClass*<br/>
Apunta al `CRuntimeClass` objeto de la clase de vista. Esta clase `CView`es una clase derivada que se define para mostrar los documentos.

### <a name="remarks"></a>Observaciones

Asigne dinámicamente `CMultiDocTemplate` un objeto para cada tipo de documento `CWinApp::AddDocTemplate` que `InitInstance` admita la aplicación y pase cada uno de ellos desde la función miembro de la clase de aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

Este es un segundo ejemplo.

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>Consulte también

[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate (clase)](../../mfc/reference/csingledoctemplate-class.md)<br/>
[Clase CWinApp](../../mfc/reference/cwinapp-class.md)
