---
title: Clase CSplitterWndEx | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs:
- C++
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a74691b17e04c20fa45045fa4105fd73925f19f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065400"
---
# <a name="csplitterwndex-class"></a>Clase CSplitterWndEx

Representa una ventana divisora personalizada.

## <a name="syntax"></a>Sintaxis

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|Constructor predeterminado.|
|`CSplitterWndEx::~CSplitterWndEx`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Lo llama el marco de trabajo para dibujar una ventana divisora. (Invalida [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>Comentarios

Invalidar el `OnDrawSplitter` método para personalizar la apariencia de los componentes gráficos de una ventana divisora.

El `CSplitterWndEx` clase se utiliza junto con el [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), y [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) métodos, que son implementado por un administrador visual. Para hacer que un administrador visual dibujar una ventana divisora en la aplicación, sustituir las declaraciones de la `CSplitterWnd` clase con la `CSplitterWndEx` clase. Para las aplicaciones de la ventana de marco, se declara la clase de ventana divisora en la clase CMainFrame que se encuentra en mainfrm.h. Para obtener un ejemplo, vea el `OutlookDemo` ejemplo en el directorio Samples.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsplitterwndex.h

##  <a name="ondrawsplitter"></a>  CSplitterWndEx::OnDrawSplitter

Lo llama el marco de trabajo para dibujar una ventana divisora.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Puntero al contexto de dispositivo. Si este parámetro es NULL, el marco de trabajo se vuelve a dibujar la ventana activa.

*nLas*<br/>
[in] Uno de los `CSplitterWnd::ESplitType` valores de enumeración que especifica el elemento de la ventana de separador se va a dibujar. Los valores válidos son `splitBox`, `splitBar`, `splitIntersection` y `splitBorder`.

*Rect*<br/>
[in] Un rectángulo delimitador que especifica las dimensiones y la ubicación para dibujar el elemento de la ventana divisora especificado.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../hierarchy-chart.md)<br/>
[Clases](mfc-classes.md)<br/>
[CSplitterWnd (clase)](csplitterwnd-class.md)<br/>
[CMFCVisualManager (clase)](cmfcvisualmanager-class.md)