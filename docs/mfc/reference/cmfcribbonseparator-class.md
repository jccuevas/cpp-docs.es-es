---
title: Clase CMFCRibbonSeparator
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
ms.openlocfilehash: 65321cb80c80a5f4c6b3cf9c67e85b1bfb6f9d11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445602"
---
# <a name="cmfcribbonseparator-class"></a>Clase CMFCRibbonSeparator

Implementa el separador de la cinta de opciones.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Construye un objeto `CMFCRibbonSeparator`.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Agrega un separador a la lista de **comandos** del cuadro de diálogo **personalizar** . (Invalida [CMFCRibbonBaseElement:: AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox)).|
|`CMFCRibbonSeparator::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCRibbonSeparator::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|

### <a name="protected-methods"></a>Métodos protegidos

|||
|-|-|
|Nombre|Descripción|
|[CMFCRibbonSeparator:: CopyFrom](#copyfrom)|Un método de copia que establece las variables miembro de un separador de otro objeto.|
|[CMFCRibbonSeparator:: GetRegularSize](#getregularsize)|Devuelve el tamaño de un separador.|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Indica si se trata de un separador.|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Indica si se trata de una tabulación.|
|[CMFCRibbonSeparator:: OnDraw](#ondraw)|Lo llama el sistema para dibujar el separador en la cinta de opciones o en la barra de herramientas de acceso rápido.|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Lo llama el sistema para dibujar el separador en la lista de **comandos** .|

## <a name="remarks"></a>Observaciones

Un separador de cinta es una línea vertical u horizontal que separa lógicamente los elementos de la cinta de opciones. Un separador se puede dibujar en el control de la cinta de opciones, en el menú principal de la aplicación, en la barra de estado de la cinta y en la barra de herramientas de acceso rápido.

Para usar un separador en la aplicación, construya el nuevo objeto y agréguelo al menú principal de la aplicación, como se muestra aquí:

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

Llame a [CMFCRibbonPanel:: AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) para agregar separadores a los paneles de la cinta de opciones. El método `AddSeparator` asigna y agrega internamente los separadores.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxbaseribbonelement.h

##  <a name="addtolistbox"></a>CMFCRibbonSeparator::AddToListBox

Agrega un separador a la lista de **comandos** del cuadro de diálogo **personalizar** .

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Parámetros

*pWndListBox*<br/>
de Puntero a la lista de **comandos** donde se agrega el separador.

*bDeep*<br/>
de Tendrán.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la cadena en el cuadro de lista especificado por *pWndListBox*.

##  <a name="cmfcribbonseparator"></a>CMFCRibbonSeparator::CMFCRibbonSeparator

Construye un objeto `CMFCRibbonSeparator`.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Parámetros

*bIsHoriz*<br/>
de Si es TRUE, el separador es horizontal; Si es FALSE, el separador es vertical.

### <a name="remarks"></a>Observaciones

Los separadores horizontales se usan en los menús de la aplicación. Los separadores verticales se usan en las barras de herramientas.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la clase `CMFCRibbonSeparator`.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCRibbonSeparator:: CopyFrom

Un método de copia que establece las variables miembro de un separador de otro objeto.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parámetros

*Diez*<br/>
de El elemento de la cinta de origen desde el que se va a copiar.

##  <a name="getregularsize"></a>CMFCRibbonSeparator:: GetRegularSize

Devuelve el tamaño de un separador.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Un puntero a un contenido de dispositivo.

### <a name="return-value"></a>Valor devuelto

Tamaño del separador en el contexto de dispositivo especificado.

##  <a name="isseparator"></a>CMFCRibbonSeparator::IsSeparator

Indica si se trata de un separador.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre es TRUE para esta clase.

##  <a name="istabstop"></a>CMFCRibbonSeparator::IsTabStop

Indica si se trata de una tabulación.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre FALSE para esta clase.

### <a name="remarks"></a>Observaciones

Un separador de la cinta de opciones no es una tabulación.

##  <a name="ondraw"></a>CMFCRibbonSeparator:: OnDraw

Lo llama el sistema para dibujar el separador en la cinta de opciones o en la barra de herramientas de acceso rápido.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Un puntero a un contexto de dispositivo.

##  <a name="ondrawonlist"></a>CMFCRibbonSeparator::OnDrawOnList

Lo llama el sistema para dibujar el separador en la lista de **comandos** .

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
|*pDC*|de Un puntero a un contexto de dispositivo.|
|*strText*|de Texto que se muestra en la lista.|
|*nTextOffset*|de Espaciado entre el texto y el lado izquierdo del rectángulo delimitador.|
|*Rect*|de Especifica el rectángulo delimitador.|
|*bIsSelected*|de Tendrán.|
|*bHighlighted*|de Tendrán.|

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
