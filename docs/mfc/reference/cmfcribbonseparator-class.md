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
ms.openlocfilehash: 05ac8b26cb6b6e7d8e622ecbaac1d4a81bfd35e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565937"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator (clase)

Implementa el separador de la cinta de opciones.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Name|Descripción|
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Construye un objeto `CMFCRibbonSeparator`.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Name|Descripción|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Agrega un separador para el **comandos** lista en el **personalizar** cuadro de diálogo. (Invalida [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|
|`CMFCRibbonSeparator::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|

### <a name="protected-methods"></a>Métodos protegidos

|||
|-|-|
|Name|Descripción|
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Un método de copia que establece las variables de miembro de un separador de otro objeto.|
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Devuelve el tamaño de un separador.|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Indica si se trata de un separador.|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Indica si se trata de una posición de tabulación.|
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Llamado por el sistema para dibujar el separador en la cinta de opciones o la barra de herramientas de acceso rápido.|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Llamado por el sistema para dibujar el separador en la **comandos** lista.|

## <a name="remarks"></a>Comentarios

Un separador de cinta es una línea vertical u horizontal que lógicamente separa la cinta de opciones elementos. En el control de la cinta de opciones, el menú principal de la aplicación, la barra de estado de la cinta de opciones y la barra de herramientas de acceso rápido, se puede dibujar un separador.

Para utilizar un separador en la aplicación, construya el objeto nuevo y agregarlo al menú principal de la aplicación como se muestra aquí:

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```
Llame a [CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) para agregar separadores a paneles de cinta. Los separadores se asignan y se agrega de forma interna el `AddSeparator` método.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxbaseribbonelement.h

##  <a name="addtolistbox"></a>  CMFCRibbonSeparator::AddToListBox

Agrega un separador para el **comandos** lista en el **personalizar** cuadro de diálogo.

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Parámetros

*pWndListBox*<br/>
[in] Un puntero a la **comandos** donde se agrega el separador de lista.

*bDeep*<br/>
[in] Pasa por alto.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la cadena en el cuadro de lista especificado por *pWndListBox*.

##  <a name="cmfcribbonseparator"></a>  CMFCRibbonSeparator::CMFCRibbonSeparator

Construye un objeto `CMFCRibbonSeparator`.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Parámetros

*bIsHoriz*<br/>
[in] Si es TRUE, el separador es horizontal; Si es FALSE, el separador es vertical.

### <a name="remarks"></a>Comentarios

Separadores horizontales se utilizan en los menús de la aplicación. Separadores verticales se utilizan en las barras de herramientas.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCRibbonSeparator` clase.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCRibbonSeparator::CopyFrom

Un método de copia que establece las variables de miembro de un separador de otro objeto.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[in] El elemento de cinta de opciones de origen para copiarlos.

##  <a name="getregularsize"></a>  CMFCRibbonSeparator::GetRegularSize

Devuelve el tamaño de un separador.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Un puntero a un contenido del dispositivo.

### <a name="return-value"></a>Valor devuelto

El tamaño del separador en el contexto de dispositivo determinado.

##  <a name="isseparator"></a>  CMFCRibbonSeparator::IsSeparator

Indica si se trata de un separador.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre TRUE para esta clase.

##  <a name="istabstop"></a>  CMFCRibbonSeparator::IsTabStop

Indica si se trata de una posición de tabulación.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre FALSE para esta clase.

### <a name="remarks"></a>Comentarios

Un separador de la cinta de opciones no es una posición de tabulación.

##  <a name="ondraw"></a>  CMFCRibbonSeparator::OnDraw

Llamado por el sistema para dibujar el separador en la cinta de opciones o la barra de herramientas de acceso rápido.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Un puntero a un contexto de dispositivo.

##  <a name="ondrawonlist"></a>  CMFCRibbonSeparator::OnDrawOnList

Llamado por el sistema para dibujar el separador en la **comandos** lista.

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
|*pDC*|[in] Un puntero a un contexto de dispositivo.|
|*strText*|[in] Texto que se muestra en la lista.|
|*nTextOffset*|[in] Espaciado entre el texto y el lado izquierdo del rectángulo delimitador.|
|*Rect*|[in] Especifica el rectángulo delimitador.|
|*bIsSelected*|[in] Pasa por alto.|
|*bHighlighted*|[in] Pasa por alto.|

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
