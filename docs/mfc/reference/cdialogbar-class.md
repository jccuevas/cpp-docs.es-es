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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883633"
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
|[CDialogBar:: CDialogBar](#cdialogbar)|Construye un objeto `CDialogBar`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDialogBar:: Create](#create)|Crea una barra de cuadro de diálogo de Windows y la adjunta al objeto `CDialogBar`.|

## <a name="remarks"></a>Comentarios

Una barra de cuadro de diálogo es similar a un cuadro de diálogo en que contiene los controles estándar de Windows con los que el usuario puede hacer tabulaciones. Otra similitud es que se crea una plantilla de cuadro de diálogo para representar la barra de cuadro de diálogo.

La creación y el uso de una barra de cuadro de diálogo es similar a la creación y el uso de un objeto `CFormView`. En primer lugar, use el [Editor de cuadros](../../windows/dialog-editor.md) de diálogo para definir una plantilla de cuadro de diálogo con el estilo WS_CHILD y ningún otro estilo. La plantilla no debe tener el estilo WS_VISIBLE. En el código de la aplicación, llame al constructor para construir el `CDialogBar` objeto y, a continuación, llame a `Create` para crear la ventana de la barra de diálogo y adjuntarla al objeto `CDialogBar`.

Para obtener más información sobre `CDialogBar`, vea las [barras de cuadro de diálogo](../../mfc/dialog-bars.md) del artículo y la [Nota técnica 31](../../mfc/tn031-control-bars.md), barras de control.

> [!NOTE]
>  En la versión actual, un objeto de `CDialogBar` no puede hospedar controles de Windows Forms. Para obtener más información sobre los controles de C++Windows Forms en visual, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext. h

##  <a name="cdialogbar"></a>CDialogBar:: CDialogBar

Construye un objeto `CDialogBar`.

```
CDialogBar();
```

##  <a name="create"></a>CDialogBar:: Create

Carga la plantilla de recursos de cuadro de diálogo especificada por `lpszTemplateName` o `nIDTemplate`, crea la ventana de la barra de diálogo, establece su estilo y la asocia al objeto `CDialogBar`.

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
Puntero al objeto `CWnd` primario.

*lpszTemplateName*<br/>
Puntero al nombre de la plantilla de recursos del cuadro de diálogo del objeto de `CDialogBar`.

*nStyle*<br/>
Estilo de la barra de herramientas. Los estilos de barra de herramientas adicionales admitidos son:

- CBRS_TOP barra de control está en la parte superior de la ventana de marco.

- CBRS_BOTTOM barra de control está en la parte inferior de la ventana de marco.

- CBRS_NOALIGN barra de control no se recoloca cuando se cambia el tamaño del elemento primario.

- CBRS_TOOLTIPS barra de control muestra información sobre herramientas.

- CBRS_SIZE_DYNAMIC barra de control es dinámica.

- CBRS_SIZE_FIXED barra de control es fija.

- CBRS_FLOATING barra de control es flotante.

- CBRS_FLYBY barra de estado muestra información sobre el botón.

- CBRS_HIDE_INPLACE barra de control no se muestra al usuario.

*nID*<br/>
IDENTIFICADOR del control de la barra de cuadro de diálogo.

*nIDTemplate*<br/>
El identificador de recurso de la plantilla de cuadro de diálogo del objeto de `CDialogBar`.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si especifica el estilo de alineación CBRS_TOP o CBRS_BOTTOM, el ancho de la barra de diálogo es el de la ventana de marco y su alto es el del recurso especificado por *nIDTemplate*. Si especifica el estilo de alineación CBRS_LEFT o CBRS_RIGHT, el alto de la barra de cuadro de diálogo es el de la ventana de marco y su ancho es el del recurso especificado por *nIDTemplate*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFormView (clase)](../../mfc/reference/cformview-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
