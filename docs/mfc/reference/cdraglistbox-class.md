---
title: CDragListBox (clase)
ms.date: 11/04/2016
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
ms.openlocfilehash: 0d1ae94948e1143a5bac17985423c4bd1bfbaf65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374030"
---
# <a name="cdraglistbox-class"></a>CDragListBox (clase)

Además de proporcionar la funcionalidad de `CDragListBox` un cuadro de lista de Windows, la clase permite al usuario mover elementos de cuadro de lista, como nombres de archivo, dentro del cuadro de lista.

## <a name="syntax"></a>Sintaxis

```
class CDragListBox : public CListBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDragListBox::CDragListBox](#cdraglistbox)|Construye un objeto `CDragListBox`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDragListBox::BeginDrag](#begindrag)|Llamado por el marco de trabajo cuando se inicia una operación de arrastre.|
|[CDragListBox::CancelDrag](#canceldrag)|Llamado por el marco de trabajo cuando se ha cancelado una operación de arrastre.|
|[CDragListBox::Darrastrar](#dragging)|Llamado por el marco de trabajo durante una operación de arrastre.|
|[CDragListBox::DrawInsert](#drawinsert)|Dibuja la guía de inserción del cuadro de lista de arrastrar.|
|[CDragListBox::Ddespertó](#dropped)|Llamado por el marco de trabajo después de que se ha quitado el elemento.|
|[CDragListBox::ItemFromPt](#itemfrompt)|Devuelve las coordenadas del elemento que se está arrastrando.|

## <a name="remarks"></a>Observaciones

Los cuadros de lista con esta capacidad permiten a los usuarios ordenar los elementos de una lista de la manera que sea más útil para ellos. De forma predeterminada, el cuadro de lista moverá el elemento a la nueva ubicación de la lista. Sin `CDragListBox` embargo, los objetos se pueden personalizar para copiar elementos en lugar de moverlos.

El control de cuadro `CDragListBox` de lista asociado a la clase no debe tener el estilo LBS_SORT o LBS_MULTIPLESELECT. Para obtener una descripción de los estilos de cuadro de lista, vea [Estilos de cuadro de lista](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Para utilizar un cuadro de lista de arrastrar en un cuadro de diálogo existente de la aplicación, agregue `Control` un control `CDragListBox`de cuadro de lista a la plantilla de cuadro de diálogo mediante el editor de cuadros de diálogo y, a continuación, asigne una variable miembro (de Categoría y Tipo de variable ) correspondiente al control de cuadro de lista de la plantilla de cuadro de diálogo.

Para obtener más información sobre la asignación de controles a variables miembro, vea [Acceso directo para definir variables miembro para controles](../../windows/defining-member-variables-for-dialog-controls.md)de cuadro de diálogo .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a>CDragListBox::BeginDrag

Llamado por el marco de trabajo cuando se produce un evento que podría iniciar una operación de arrastre, como presionar el botón izquierdo del mouse.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
Un objeto [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) que contiene las coordenadas del elemento que se está arrastrando.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se permite arrastrar, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Invalide esta función si desea controlar lo que sucede cuando comienza una operación de arrastre. La implementación predeterminada captura el mouse y permanece en modo de arrastre hasta que el usuario hace clic en el botón izquierdo o derecho del ratón o presiona ESC, momento en el que se cancela la operación de arrastre.

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a>CDragListBox::CancelDrag

Llamado por el marco de trabajo cuando se ha cancelado una operación de arrastre.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
Un objeto [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) que contiene las coordenadas del elemento que se está arrastrando.

### <a name="remarks"></a>Observaciones

Reemplace esta función para controlar cualquier procesamiento especial para el control del cuadro de lista.

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a>CDragListBox::CDragListBox

Construye un objeto `CDragListBox`.

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a>CDragListBox::Darrastrar

Llamado por el marco de trabajo cuando se `CDragListBox` arrastra un elemento de cuadro de lista dentro del objeto.

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
Objeto [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) que contiene las coordenadas de pantalla x e y del cursor.

### <a name="return-value"></a>Valor devuelto

El identificador de recurso del cursor que se va a mostrar. Los siguientes valores son posibles:

- DL_COPYCURSOR Indica que se copiará el elemento.

- DL_MOVECURSOR Indica que se moverá el elemento.

- DL_STOPCURSOR Indica que el destino de colocación actual no es aceptable.

### <a name="remarks"></a>Observaciones

El comportamiento predeterminado devuelve DL_MOVECURSOR. Reemplace esta función si desea proporcionar funcionalidad adicional.

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a>CDragListBox::DrawInsert

Llamado por el marco de trabajo para dibujar la guía de inserción antes del elemento con el índice indicado.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
El índice de base cero del punto de inserción.

### <a name="remarks"></a>Observaciones

Un valor de - 1 borra la guía de inserción. Reemplace esta función para modificar la apariencia o el comportamiento de la guía de inserción.

## <a name="cdraglistboxdropped"></a><a name="dropped"></a>CDragListBox::Ddespertó

Llamado por el marco de trabajo `CDragListBox` cuando se coloca un elemento dentro de un objeto.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Parámetros

*nSrcIndex*<br/>
Especifica el índice de base cero de la cadena descartada.

*Pt*<br/>
Un [objeto CPoint](../../atl-mfc-shared/reference/cpoint-class.md) que contiene las coordenadas del sitio de colocación.

### <a name="remarks"></a>Observaciones

El comportamiento predeterminado copia el elemento de cuadro de lista y sus datos en la nueva ubicación y, a continuación, elimina el elemento original. Reemplace esta función para personalizar el comportamiento predeterminado, como habilitar copias de elementos de cuadro de lista que se arrastrarán a otras ubicaciones dentro de la lista.

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a>CDragListBox::ItemFromPt

Llame a esta función para recuperar el índice de base cero del elemento de cuadro de lista ubicado en *pt*.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
Objeto [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) que contiene las coordenadas de un punto dentro del cuadro de lista.

*bAutoScroll*<br/>
Distinto de cero si se permite el desplazamiento, de lo contrario 0.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento del cuadro de lista de arrastre.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)
