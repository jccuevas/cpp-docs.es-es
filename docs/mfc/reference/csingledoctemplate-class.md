---
title: CSingleDocTemplate (clase)
ms.date: 11/04/2016
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
ms.openlocfilehash: 5a014b35a6cd2d12367e190e4d6dd689e28eae66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318349"
---
# <a name="csingledoctemplate-class"></a>CSingleDocTemplate (clase)

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

## <a name="remarks"></a>Observaciones

Una aplicación SDI utiliza la ventana de marco principal para mostrar un documento; solo se puede abrir un documento a la vez.

Una plantilla de documento define la relación entre tres tipos de clases:

- Una clase de documento, `CDocument`de la que se deriva .

- Una clase de vista, que muestra los datos de la clase de documento enumerada anteriormente. Puede derivar esta `CView`clase `CScrollView` `CFormView`de `CEditView`, , , o . (También puede `CEditView` utilizar directamente.)

- Una clase de ventana de marco, que contiene la vista. Para una plantilla de documento SDI, `CFrameWnd`puede derivar esta clase de ; si no necesita personalizar el comportamiento de la ventana `CFrameWnd` de marco principal, puede utilizar directamente sin derivar su propia clase.

Una aplicación SDI normalmente admite un tipo de `CSingleDocTemplate` documento, por lo que solo tiene un objeto. Solo se puede abrir un documento a la vez.

No es necesario llamar a ninguna `CSingleDocTemplate` función miembro de excepto el constructor. El marco `CSingleDocTemplate` de trabajo controla los objetos internamente.

Para obtener más `CSingleDocTemplate`información sobre el uso de , consulte Plantillas de documento y Proceso de creación de [documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a>CSingleDocTemplate::CSingleDocTemplate

Construye un objeto `CSingleDocTemplate`.

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parámetros

*nIDResource*<br/>
Especifica el identificador de los recursos utilizados con el tipo de documento. Esto puede incluir menú, icono, tabla de aceleradores y recursos de cadena.

El recurso de cadena consta de hasta siete subcadenas separadas por el carácter ''n' (se necesita el carácter ''n' como marcador de posición si no se incluye una subcadena; sin embargo, no es necesario seguir los caracteres 'n'); estas subcadenas describen el tipo de documento. Para obtener información acerca de las subcadenas, vea [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Este recurso de cadena se encuentra en el archivo de recursos de la aplicación. Por ejemplo:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

Puede editar esta cadena mediante el editor de cadenas; toda la cadena aparece como una sola entrada en el Editor de cadenas, no como siete entradas independientes.

Para obtener más información acerca de estos tipos de recursos, vea el Editor de [cadenas](../../windows/string-editor.md).

*pDocClass*<br/>
Apunta al `CRuntimeClass` objeto de la clase de documento. Esta clase `CDocument`es una clase derivada que se define para representar los documentos.

*pFrameClass*<br/>
Apunta al `CRuntimeClass` objeto de la clase de ventana de marco. Esta clase puede `CFrameWnd`ser una clase derivada, `CFrameWnd` o puede ser en sí misma si desea un comportamiento predeterminado para la ventana de marco principal.

*pViewClass*<br/>
Apunta al `CRuntimeClass` objeto de la clase de vista. Esta clase `CView`es una clase derivada que se define para mostrar los documentos.

### <a name="remarks"></a>Observaciones

Asigne dinámicamente `CSingleDocTemplate` un objeto y `CWinApp::AddDocTemplate` páselo desde la función miembro de la `InitInstance` clase de aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>Consulte también

[EJEMPLO DE MFC DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[CMultiDocTemplate (clase)](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[Clase CWinApp](../../mfc/reference/cwinapp-class.md)
