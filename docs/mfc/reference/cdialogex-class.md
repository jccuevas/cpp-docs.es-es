---
title: CDialogEx (clase)
ms.date: 11/04/2016
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
ms.openlocfilehash: 717e560035d42957c16168097577d0c8c589e3c7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753352"
---
# <a name="cdialogex-class"></a>CDialogEx (clase)

La clase `CDialogEx` especifica el color de fondo y la imagen de fondo de un cuadro de diálogo.

## <a name="syntax"></a>Sintaxis

```
class CDialogEx : public CDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|Construye un objeto `CDialogEx`.|
|`CDialogEx::~CDialogEx`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|Establece el color de fondo del cuadro de diálogo.|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Establece la imagen de fondo del cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

Para usar la clase `CDialogEx`, derive la clase de cuadro de diálogo de la clase `CDialogEx`, en lugar de derivarla de la clase `CDialog`.

Las imágenes del cuadro de diálogo se almacenan en un archivo de recursos. El marco de trabajo elimina automáticamente cualquier imagen que se cargue desde el archivo de recursos. Para eliminar mediante programación la imagen de fondo actual, llame a `OnDestroy` la [CDialogEx::SetBackgroundImage](#setbackgroundimage) método o implementar un controlador de eventos. Cuando se llama a la [CDialogEx::SetBackgroundImage](#setbackgroundimage) método, pase un `HBITMAP` parámetro como el identificador de imagen. El objeto `CDialogEx` tomará posesión de la imagen y la elimina si la marca `m_bAutoDestroyBmp` es `TRUE`.

Un `CDialogEx` objeto puede ser un elemento primario de un [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) objeto. El [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) `CDialogEx::SetActiveMenu` objeto llama al método cuando se abre el [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) objeto. Después, `CDialogEx` el objeto controla cualquier evento de menú hasta que se cierra el objeto [CMFCPopupMenu (clase).](../../mfc/reference/cmfcpopupmenu-class.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdialogex.h

## <a name="cdialogexcdialogex"></a><a name="cdialogex"></a>CDialogEx::CDialogEx

Construye un objeto `CDialogEx`.

```
CDialogEx(
    UINT nIDTemplate,
    CWnd* pParent=NULL);

CDialogEx(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd=NULL);
```

### <a name="parameters"></a>Parámetros

*nIDTemplate*<br/>
[en] El identificador de recurso de una plantilla de cuadro de diálogo.

*lpszTemplateName*<br/>
[en] El nombre de recurso de una plantilla de cuadro de diálogo.

*pParent*<br/>
[en] Un puntero a la ventana primaria. El valor predeterminado es NULL.

*pParentWnd*<br/>
[en] Un puntero a la ventana primaria. El valor predeterminado es NULL.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdialogexsetbackgroundcolor"></a><a name="setbackgroundcolor"></a>CDialogEx::SetBackgroundColor

Establece el color de fondo del cuadro de diálogo.

```cpp
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[en] Un valor de color RGB.

*bRepaint*<br/>
[en] TRUE para actualizar inmediatamente la pantalla; de lo contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

## <a name="cdialogexsetbackgroundimage"></a><a name="setbackgroundimage"></a>CDialogEx::SetBackgroundImage

Establece la imagen de fondo del cuadro de diálogo.

```cpp
void SetBackgroundImage(
    HBITMAP hBitmap,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bAutoDestroy=TRUE,
    BOOL bRepaint=TRUE);

BOOL SetBackgroundImage(
    UINT uiBmpResId,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
[en] Un identificador de la imagen de fondo.

*uiBmpResId*<br/>
[en] El identificador de recurso de la imagen de fondo.

*ubicación*<br/>
[en] Uno de `CDialogEx::BackgroundLocation` los valores que especifican la ubicación de la imagen. Los valores válidos incluyen BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT y BACKGR_BOTTOMRIGHT. El valor predeterminado es BACKGR_TILE.

*bAutoDestroy*<br/>
[en] TRUE para destruir automáticamente la imagen de fondo; de lo contrario, FALSE.

*bRepaint*<br/>
[en] TRUE para volver a dibujar inmediatamente el cuadro de diálogo; de lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

En la segunda sintaxis de sobrecarga de método, TRUE si el método es correcto; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

La imagen que especifique no se estira para ajustarse al área de cliente del cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[CContextMenuManager (clase)](../../mfc/reference/ccontextmenumanager-class.md)
