---
title: CDialogEx (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
dev_langs:
- C++
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02a8ae81ea94c47cd11beae0b3ed0eacee77db07
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386306"
---
# <a name="cdialogex-class"></a>CDialogEx (clase)

La clase `CDialogEx` especifica el color de fondo y la imagen de fondo de un cuadro de diálogo.

## <a name="syntax"></a>Sintaxis

```
class CDialogEx : public CDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|Construye un objeto `CDialogEx`.|
|`CDialogEx::~CDialogEx`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|Establece el color de fondo del cuadro de diálogo.|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Establece la imagen de fondo del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Para usar la clase `CDialogEx`, derive la clase de cuadro de diálogo de la clase `CDialogEx`, en lugar de derivarla de la clase `CDialog`.

Las imágenes del cuadro de diálogo se almacenan en un archivo de recursos. El marco de trabajo elimina automáticamente cualquier imagen que se cargue desde el archivo de recursos. Para eliminar mediante programación la imagen de fondo actual, llame a la [CDialogEx::SetBackgroundImage](#setbackgroundimage) método o implemente un `OnDestroy` controlador de eventos. Cuando se llama a la [CDialogEx::SetBackgroundImage](#setbackgroundimage) método, pase un `HBITMAP` parámetro como identificador de la imagen. El objeto `CDialogEx` tomará posesión de la imagen y la elimina si la marca `m_bAutoDestroyBmp` es `TRUE`.

Un `CDialogEx` objeto puede ser un elemento primario de un [CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md) objeto. El [CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md) de objeto llama el `CDialogEx::SetActiveMenu` método cuando el [CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md) objeto se abre. A continuación, el `CDialogEx` objeto controla cualquier evento de menú hasta que el [CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md) objeto está cerrado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdialogex.h

##  <a name="cdialogex"></a>  CDialogEx::CDialogEx

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
[in] El identificador de recurso de una plantilla de cuadro de diálogo.

*lpszTemplateName*<br/>
[in] El nombre de recurso de una plantilla de cuadro de diálogo.

*pParent*<br/>
[in] Un puntero a la ventana primaria. El valor predeterminado es NULL.

*pParentWnd*<br/>
[in] Un puntero a la ventana primaria. El valor predeterminado es NULL.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="setbackgroundcolor"></a>  CDialogEx::SetBackgroundColor

Establece el color de fondo del cuadro de diálogo.

```
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[in] Un valor de color RGB.

*bRepaint*<br/>
[in] TRUE para actualizar inmediatamente la pantalla; en caso contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

##  <a name="setbackgroundimage"></a>  CDialogEx::SetBackgroundImage

Establece la imagen de fondo del cuadro de diálogo.

```
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
[in] Identificador de la imagen de fondo.

*uiBmpResId*<br/>
[in] El identificador de recurso de la imagen de fondo.

*Ubicación*<br/>
[in] Uno de los `CDialogEx::BackgroundLocation` valores que especifican la ubicación de la imagen. Los valores válidos incluyen BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT y BACKGR_BOTTOMRIGHT. El valor predeterminado es BACKGR_TILE.

*bAutoDestroy*<br/>
[in] TRUE para destruir automáticamente la imagen de fondo. en caso contrario, FALSE.

*bRepaint*<br/>
[in] TRUE para volver a dibujar inmediatamente el cuadro de diálogo; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

En el segundo método sobrecargar sintaxis, TRUE si el método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

La imagen que especifique no se ajusta para ajustar el área de cliente del cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[CContextMenuManager (clase)](../../mfc/reference/ccontextmenumanager-class.md)
