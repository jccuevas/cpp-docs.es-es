---
title: CMFCRibbonSeparator (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
ms.openlocfilehash: 41a958c78719f6aedf1cc02f8e3ff5a2dbbf0e1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368848"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator (clase)

Implementa el separador de cinta de opciones.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Construye un objeto `CMFCRibbonSeparator`.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Agrega un separador a la lista **Comandos** del cuadro de diálogo **Personalizar.** (Reemplaza [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCRibbonSeparator::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|

### <a name="protected-methods"></a>Métodos protegidos

|||
|-|-|
|Nombre|Descripción|
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Método copy que establece las variables miembro de un separador desde otro objeto.|
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Devuelve el tamaño de un separador.|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Indica si se trata de un separador.|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Indica si se trata de una tabulación.|
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Llamado por el sistema para dibujar el separador en la cinta de opciones o la barra de herramientas de acceso rápido.|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Llamado por el sistema para dibujar el separador en la lista **Comandos.**|

## <a name="remarks"></a>Observaciones

Un separador de cinta de opciones es una línea vertical u horizontal que separa lógicamente los elementos de la cinta de opciones. Se puede dibujar un separador en el control de la cinta de opciones, el menú principal de la aplicación, la barra de estado de la cinta de opciones y la barra de herramientas de acceso rápido.

Para utilizar un separador en la aplicación, construya el nuevo objeto y agréguelo al menú principal de la aplicación como se muestra aquí:

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

Llame a [CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) para agregar separadores a los paneles de la cinta de opciones. Los separadores se asignan y `AddSeparator` se agregan internamente por el método.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a>CMFCRibbonSeparator::AddToListBox

Agrega un separador a la lista **Comandos** del cuadro de diálogo **Personalizar.**

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Parámetros

*pWndListBox*<br/>
[en] Puntero a la lista **Comandos** donde se agrega el separador.

*bDeep*<br/>
[en] Ignorado.

### <a name="return-value"></a>Valor devuelto

Indice de base cero a la cadena en el cuadro de lista especificado por *pWndListBox*.

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a>CMFCRibbonSeparator::CMFCRibbonSeparator

Construye un objeto `CMFCRibbonSeparator`.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Parámetros

*bIsHoriz*<br/>
[en] Si TRUE, el separador es horizontal; si FALSE, el separador es vertical.

### <a name="remarks"></a>Observaciones

Los separadores horizontales se utilizan en los menús de la aplicación. Los separadores verticales se utilizan en las barras de herramientas.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCRibbonSeparator` cómo construir un objeto de la clase.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonSeparator::CopyFrom

Método copy que establece las variables miembro de un separador desde otro objeto.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parámetros

*Fuente*<br/>
[en] El elemento de la cinta de opciones de origen desde el que se va a copiar.

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonSeparator::GetRegularSize

Devuelve el tamaño de un separador.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Un puntero al contenido de un dispositivo.

### <a name="return-value"></a>Valor devuelto

El tamaño del separador en el contexto del dispositivo dado.

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a>CMFCRibbonSeparator::IsSeparator

Indica si se trata de un separador.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre TRUE para esta clase.

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a>CMFCRibbonSeparator::IsTabStop

Indica si se trata de una tabulación.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre FALSE para esta clase.

### <a name="remarks"></a>Observaciones

Un separador de cinta de opciones no es una tabulación.

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a>CMFCRibbonSeparator::OnDraw

Llamado por el sistema para dibujar el separador en la cinta de opciones o la barra de herramientas de acceso rápido.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonSeparator::OnDrawOnList

Llamado por el sistema para dibujar el separador en la lista **Comandos.**

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDC*|[en] Puntero a un contexto de dispositivo.|
|*strText*|[en] Texto mostrado en la lista.|
|*nTextOffset*|[en] Espaciado entre el texto y el lado izquierdo del rectángulo delimitador.|
|*Rect*|[en] Especifica el rectángulo delimitador.|
|*bIsSelected*|[en] Ignorado.|
|*bResaltado*|[en] Ignorado.|

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
