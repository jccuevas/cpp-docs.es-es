---
title: Clase CMFCRibbonGalleryMenuButton
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CopyFrom
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CreatePopupMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::GetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::HasButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed
helpviewer_keywords:
- CMFCRibbonGalleryMenuButton [MFC], CMFCRibbonGalleryMenuButton
- CMFCRibbonGalleryMenuButton [MFC], CopyFrom
- CMFCRibbonGalleryMenuButton [MFC], CreatePopupMenu
- CMFCRibbonGalleryMenuButton [MFC], GetPalette
- CMFCRibbonGalleryMenuButton [MFC], HasButton
- CMFCRibbonGalleryMenuButton [MFC], IsEmptyMenuAllowed
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
ms.openlocfilehash: 0ec295fa64b835064435992a398d4292ccf26f38
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866153"
---
# <a name="cmfcribbongallerymenubutton-class"></a>Clase CMFCRibbonGalleryMenuButton

Implementa un botón de menú de la cinta que contiene galerías de la cinta.
Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](#cmfcribbongallerymenubutton)|Construye e inicializa un objeto `CMFCRibbonGalleryMenuButton`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCRibbonGalleryMenuButton::CopyFrom](#copyfrom)|(Invalida [CMFCToolBarMenuButton:: CopyFrom](../../mfc/reference/cmfctoolbarmenubutton-class.md#copyfrom)).|
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](#createpopupmenu)|(Invalida [CMFCToolBarMenuButton:: CreatePopupMenu](../../mfc/reference/cmfctoolbarmenubutton-class.md#createpopupmenu)).|
|[CMFCRibbonGalleryMenuButton::GetPalette](#getpalette)||
|[CMFCRibbonGalleryMenuButton::HasButton](#hasbutton)|(Invalida `CMFCToolBarMenuButton::HasButton`).|
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|(Invalida [CMFCToolBarMenuButton:: IsEmptyMenuAllowed](../../mfc/reference/cmfctoolbarmenubutton-class.md#isemptymenuallowed)).|

### <a name="remarks"></a>Comentarios

El botón de menú de la galería se muestra como un menú emergente con una flecha. Cuando el usuario hace clic en este botón, se abre una galería de imágenes. Cuando se crea un botón de menú de la galería, hay que especificar una lista de imágenes que contenga esas imágenes.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo mostrar una galería de viñetas en un botón de menú:

```cpp
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)
{
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);

    if (nBulletIndex>= 0)
    {
        CMFCToolBarButton* pExButton =
        pMenuBar->GetButton(nBulletIndex);
        ASSERT_VALID (pExButton);

        CMFCRibbonGalleryMenuButton paletteBullet (
        pExButton->m_nID,
        pExButton->GetImage (),
        pExButton->m_strText);

        InitBulletPalette (&paletteBullet.GetPalette ());

        pMenuBar->ReplaceButton (ID_PARA_BULLETS,
        paletteBullet);
    }
}
```

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonPaletteGallery. h

##  <a name="copyfrom"></a>CMFCRibbonGalleryMenuButton:: CopyFrom

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

de *src*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="cmfcribbongallerymenubutton"></a>  CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton

Construye e inicializa un objeto [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md) .

```
CMFCRibbonGalleryMenuButton(
    UINT uiID,
    int iImage,
    LPCTSTR lpszText,
    CMFCToolBarImages& imagesPalette);

CMFCRibbonGalleryMenuButton(
    UINT uiID,
    int iImage,
    LPCTSTR lpszText,
    UINT uiImagesPaletteResID = 0,
    int cxPaletteImage = 0);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
IDENTIFICADOR de comando del botón. Este es el valor enviado en el mensaje WM_COMMAND cuando el usuario hace clic en este botón.

*iImage*<br/>
Índice de la imagen que se va a mostrar con el botón de menú de la galería. Las imágenes se almacenan en el parámetro *imagesPalette* .

*lpszText*<br/>
Texto que se va a mostrar en el botón de menú.

*imagesPalette*<br/>
Contiene la lista de imágenes que se van a mostrar en la galería.

*uiImagesPaletteResID*<br/>
El identificador de recurso de la lista de imágenes para las imágenes que se van a mostrar en la galería.

*cxPaletteImage*<br/>
Especifica el ancho en píxeles de la imagen que se va a mostrar en la galería.

### <a name="remarks"></a>Comentarios

El botón de menú Galería se muestra como un menú emergente con una flecha. Cuando el usuario hace clic en este botón, se abre una galería de imágenes.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar el constructor de `CMFCRibbonGalleryMenuButton` la clase. Este fragmento de código forma parte del [ejemplo de demostración de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#8](../../mfc/reference/codesnippet/cpp/cmfcribbongallerymenubutton-class_1.cpp)]

##  <a name="createpopupmenu"></a>  CMFCRibbonGalleryMenuButton::CreatePopupMenu

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getpalette"></a>  CMFCRibbonGalleryMenuButton::GetPalette

```
CMFCRibbonGallery& GetPalette();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="hasbutton"></a>  CMFCRibbonGalleryMenuButton::HasButton

```
virtual BOOL HasButton() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isemptymenuallowed"></a>  CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarMenuButton (clase)](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[CMFCRibbonGallery (clase)](../../mfc/reference/cmfcribbongallery-class.md)
