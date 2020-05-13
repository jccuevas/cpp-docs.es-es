---
title: Clase CSplitterWndEx
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: d7952e3082bf68cff7ad9ba218073081ee522320
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363920"
---
# <a name="csplitterwndex-class"></a>Clase CSplitterWndEx

Representa una ventana divisora personalizada.

## <a name="syntax"></a>Sintaxis

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|Constructor predeterminado.|
|`CSplitterWndEx::~CSplitterWndEx`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Llamado por el marco de trabajo para dibujar una ventana divisora. (Reemplaza [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>Observaciones

Invalide `OnDrawSplitter` el método para personalizar la apariencia de los componentes gráficos de una ventana divisora.

La `CSplitterWndEx` clase se utiliza junto con los métodos [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)y [OnFillSplitterBackground,](cmfcvisualmanager-class.md#onfillsplitterbackground) que implementa un administrador visual. Para hacer que un administrador visual dibuje una ventana `CSplitterWnd` divisora `CSplitterWndEx` en la aplicación, reemplace las declaraciones de la clase por la clase. Para las aplicaciones de ventana de marco, la clase de ventana divisora se declara en la clase CMainFrame que se encuentra en mainfrm.h. Para obtener un `OutlookDemo` ejemplo, vea el ejemplo en el directorio Samples.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsplitterwndex.h

## <a name="csplitterwndexondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter

Llamado por el marco de trabajo para dibujar una ventana divisora.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero al contexto del dispositivo. Si este parámetro es NULL, el marco de trabajo vuelve a dibujar la ventana activa.

*nType*<br/>
[en] Uno de `CSplitterWnd::ESplitType` los valores de enumeración que especifica el elemento de ventana divisora que se va a dibujar. Los valores válidos son `splitBox`, `splitBar`, `splitIntersection` y `splitBorder`.

*Rect*<br/>
[en] Un rectángulo delimitador que especifica las dimensiones y la ubicación para dibujar el elemento de ventana divisora especificado.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../hierarchy-chart.md)<br/>
[Clases](mfc-classes.md)<br/>
[Clase CSplitterWnd](csplitterwnd-class.md)<br/>
[CMFCVisualManager (Clase)](cmfcvisualmanager-class.md)
