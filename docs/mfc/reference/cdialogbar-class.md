---
title: CDialogBar (clase)
ms.date: 11/04/2016
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
ms.openlocfilehash: af84c5239a9cb3cbddb1ab4f0230e5b1a3373573
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768307"
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

Una barra de cuadro de diálogo es similar a un cuadro de diálogo que contiene los controles de Windows estándar que el usuario puede tabular entre. Similitud otra es crear una plantilla de cuadro de diálogo para representar la barra de cuadro de diálogo.

Creación y uso de una barra de cuadro de diálogo son similar a crear y usar un `CFormView` objeto. En primer lugar, use el [editor de cuadro de diálogo](../../windows/dialog-editor.md) para definir una plantilla de cuadro de diálogo con el estilo WS_CHILD y ningún otro estilo. La plantilla no debe tener el estilo WS_VISIBLE. En el código de aplicación, llame al constructor para construir el `CDialogBar` objeto y, después, llamar a `Create` para crear la ventana de la barra de cuadro de diálogo y adjuntarlo a la `CDialogBar` objeto.

Para obtener más información sobre `CDialogBar`, consulte el artículo [barras de cuadro de diálogo](../../mfc/dialog-bars.md) y [Nota técnica 31](../../mfc/tn031-control-bars.md), barras de Control.

> [!NOTE]
>  En la versión actual, un `CDialogBar` objeto no puede hospedar controles de formularios Windows Forms. Para obtener más información acerca de los controles de Windows Forms en Visual C++, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

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

Carga la plantilla de recursos de cuadro de diálogo especificada por `lpszTemplateName` o `nIDTemplate`, crea la ventana de la barra de cuadro de diálogo, se establece el estilo y lo asocia a la `CDialogBar` objeto.

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

*pParentWnd*<br/>
Un puntero al elemento primario `CWnd` objeto.

*lpszTemplateName*<br/>
Un puntero al nombre de la `CDialogBar` plantilla de recursos de cuadro de diálogo del objeto.

*nStyle*<br/>
El estilo de barra de herramientas. Estilos de barra de herramientas adicionales compatibles son:

- Barra de Control de CBRS_TOP está en la parte superior de la ventana de marco.

- Barra de Control CBRS_BOTTOM es en parte inferior de la ventana de marco.

- Barra de Control CBRS_NOALIGN no se cambia de posición cuando se cambia el tamaño del elemento primario.

- Barra de Control CBRS_TOOLTIPS muestra información sobre herramientas.

- Barra de Control CBRS_SIZE_DYNAMIC es dinámico.

- Barra de Control CBRS_SIZE_FIXED es fijo.

- Barra de Control CBRS_FLOATING está flotando.

- Barra de estado CBRS_FLYBY muestra información sobre el botón.

- Barra de Control CBRS_HIDE_INPLACE no se muestra al usuario.

*nID*<br/>
El identificador de control de la barra de cuadro de diálogo.

*nIDTemplate*<br/>
El identificador de recurso de la `CDialogBar` de plantilla de cuadro de diálogo del objeto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si especifica el estilo de alineación CBRS_TOP o CBRS_BOTTOM, es el ancho de la barra de cuadro de diálogo de la ventana de marco y su alto es el de recurso especificado por *nIDTemplate*. Si especifica el estilo de alineación CBRS_LEFT o CBRS_RIGHT, es el alto de la barra de cuadro de diálogo de la ventana de marco y su ancho sea el del recurso especificado por *nIDTemplate*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Vea también

[CTRLBARS de ejemplo](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFormView (clase)](../../mfc/reference/cformview-class.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)
