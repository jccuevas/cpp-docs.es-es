---
title: Clase CDialogBar
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
ms.openlocfilehash: cf9a2658807959108b3bb0af672d4c1835b58bc5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375677"
---
# <a name="cdialogbar-class"></a>Clase CDialogBar

Proporciona la funcionalidad de un cuadro de diálogo no modal de Windows en una barra de controles.

## <a name="syntax"></a>Sintaxis

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDialogBar::CDialogBar](#cdialogbar)|Construye un objeto `CDialogBar`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDialogBar::Crear](#create)|Crea una barra de diálogo de `CDialogBar` Windows y la adjunta al objeto.|

## <a name="remarks"></a>Observaciones

Una barra de diálogo se asemeja a un cuadro de diálogo en el que contiene controles estándar de Windows entre los que el usuario puede tabular. Otra similitud es que se crea una plantilla de cuadro de diálogo para representar la barra de diálogo.

Crear y utilizar una barra de diálogo `CFormView` es similar a crear y utilizar un objeto. En primer lugar, utilice el editor de [cuadros](../../windows/dialog-editor.md) de diálogo para definir una plantilla de cuadro de diálogo con el estilo WS_CHILD y ningún otro estilo. La plantilla no debe tener el estilo WS_VISIBLE. En el código de la aplicación, llame al constructor para construir el `CDialogBar` objeto y, a continuación, llame `Create` para crear la ventana de barra de diálogo y adjuntarlo al `CDialogBar` objeto.

Para obtener `CDialogBar`más información sobre , consulte el artículo Barras de [diálogo](../../mfc/dialog-bars.md) y [Nota técnica 31](../../mfc/tn031-control-bars.md), Barras de control.

> [!NOTE]
> En la versión `CDialogBar` actual, un objeto no puede hospedar controles de formularios Windows Forms. Para obtener más información acerca de los controles de formularios Windows Forms en Visual C++, vea Uso de un control de usuario de [formulario Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="cdialogbarcdialogbar"></a><a name="cdialogbar"></a>CDialogBar::CDialogBar

Construye un objeto `CDialogBar`.

```
CDialogBar();
```

## <a name="cdialogbarcreate"></a><a name="create"></a>CDialogBar::Crear

Carga la plantilla de recursos `lpszTemplateName` de `nIDTemplate`cuadro de diálogo especificada por o , crea `CDialogBar` la ventana de la barra de diálogo, establece su estilo y lo asocia con el objeto.

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
Un puntero al `CWnd` objeto primario.

*lpszTemplateName*<br/>
Puntero al nombre de `CDialogBar` la plantilla de recursos del cuadro de diálogo del objeto.

*nStyle*<br/>
El estilo de la barra de herramientas. Los estilos de barra de herramientas adicionales admitidos son:

- CBRS_TOP barra de control está en la parte superior de la ventana de marco.

- CBRS_BOTTOM barra de control se encuentra en la parte inferior de la ventana de marco.

- CBRS_NOALIGN barra de control no se cambia de posición cuando se cambia el tamaño del elemento primario.

- CBRS_TOOLTIPS barra control muestra las sugerencias de herramientas.

- CBRS_SIZE_DYNAMIC barra de control es dinámica.

- CBRS_SIZE_FIXED barra de control está fija.

- CBRS_FLOATING barra de control está flotante.

- CBRS_FLYBY barra Estado muestra información sobre el botón.

- CBRS_HIDE_INPLACE barra de control no se muestra al usuario.

*nID*<br/>
El identificador de control de la barra de diálogo.

*nIDTemplate*<br/>
El identificador de `CDialogBar` recurso de la plantilla de cuadro de diálogo del objeto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Si especifica el estilo de alineación CBRS_TOP o CBRS_BOTTOM, el ancho de la barra de diálogo es el de la ventana de marco y su alto es el del recurso especificado por *nIDTemplate*. Si especifica el estilo de alineación CBRS_LEFT o CBRS_RIGHT, el alto de la barra de diálogo es el de la ventana de marco y su ancho es el del recurso especificado por *nIDTemplate*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Consulte también

[CTRLBARS de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CFormView](../../mfc/reference/cformview-class.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)
