---
title: CMFCToolBarComboBoxEdit (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
helpviewer_keywords:
- CMFCToolBarComboBoxEdit [MFC], CMFCToolBarComboBoxEdit
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
ms.openlocfilehash: fcf89623fcde2067f2def83f1e491db015375e02
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280542"
---
# <a name="cmfctoolbarcomboboxedit-class"></a>CMFCToolBarComboBoxEdit (clase)

El marco de trabajo usa el `CMFCToolBarComboBoxEdit` clase para crear un botón de barra de herramientas que se comporta como un control de cuadro combinado editable.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarComboBoxEdit : public CEdit
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](#cmfctoolbarcomboboxedit)|Construye un objeto `CMFCToolBarComboBoxEdit`.|
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|Traduce los mensajes de ventana antes de enviarlos a la [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funciones de Windows. (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|

### <a name="remarks"></a>Comentarios

Derive una clase de la `CMFCToolBarComboBoxEdit` clase para personalizar sus operaciones de edición.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarcomboboxbutton.h

##  <a name="cmfctoolbarcomboboxedit"></a>  CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit

Construye un objeto `CMFCToolBarComboBoxEdit`.

```
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```

### <a name="parameters"></a>Parámetros

*combo*<br/>
[in] Una referencia a un [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objeto, que es un botón de barra de herramientas que contiene un control de cuadro combinado.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCToolBarComboBoxEdit` clase. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarComboBoxButton (clase)](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
