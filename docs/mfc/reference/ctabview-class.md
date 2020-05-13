---
title: CTabView (clase)
ms.date: 11/04/2016
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
ms.openlocfilehash: ad30cbbf5de195708d2d357a76c38b661d095c2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365923"
---
# <a name="ctabview-class"></a>CTabView (clase)

La `CTabView` clase simplifica el uso de la clase de control de ficha ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) en aplicaciones que usan la arquitectura de documento/vista de MFC.

## <a name="syntax"></a>Sintaxis

```
class CTabbedView : public CView
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTabView::AddView](#addview)|Agrega una nueva vista al control de ficha.|
|[CTabView::FindTab](#findtab)|Devuelve el índice de la vista especificada en el control de ficha.|
|[CTabView::GetActiveView](#getactiveview)|Devuelve un puntero a la vista activa actualmente|
|[CTabView::GetTabControl](#gettabcontrol)|Devuelve una referencia al control de ficha asociado a la vista.|
|[CTabView::RemoveView](#removeview)|Quita la vista del control de ficha.|
|[CTabView::SetActiveView](#setactiveview)|Activa una vista.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CTabView::IsScrollBar](#isscrollbar)|Llamado por el marco de trabajo al crear una vista de ficha para determinar si la vista de ficha tiene una barra de desplazamiento horizontal compartida.|
|[CTabView::OnActivateView](#onactivateview)|Llamado por el marco de trabajo cuando la vista de ficha se activa o inactiva.|

## <a name="remarks"></a>Observaciones

Esta clase facilita la colocación de una vista con pestañas en una aplicación de documento/vista. `CTabView`es `CView`una clase derivada que contiene `CMFCTabCtrl` un objeto incrustado. `CTabView`controla todos los `CMFCTabCtrl` mensajes necesarios para admitir el objeto. Simplemente derive una `CTabView` clase de la aplicación `CView`y conéctela a `AddView` ella y, a continuación, agregue clases derivadas mediante el método. El control de ficha mostrará esas vistas como fichas.

Por ejemplo, puede tener un documento que se puede representar de diferentes maneras: como una hoja de cálculo, un gráfico, un formulario editable, etc. Puede crear vistas individuales dibujando los datos `CTabView`según sea necesario, insertarlos en el objeto derivado y tenerlos tabulados sin ningún tipo de codificación adicional.

Ejemplo de [TabbedView: Aplicación](../../overview/visual-cpp-samples.md) de `CTabView`vista con pestañas MFC ilustra el uso de .

## <a name="example"></a>Ejemplo

En el ejemplo `CTabView` siguiente se muestra cómo se usa en el TabbedView ejemplo.

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxTabView.h

## <a name="ctabviewaddview"></a><a name="addview"></a>CTabView::AddView

Agrega una vista al control de ficha.

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Parámetros

*pViewClass*<br/>
[en] Puntero a una clase en tiempo de ejecución de la vista insertada.

*strViewLabel*<br/>
[en] Especifica el texto de la ficha.

*iIndex*<br/>
[en] Especifica la posición de base cero en la que se va a insertar la vista. Si la posición es -1, la nueva pestaña se inserta al final.

*pContext*<br/>
[en] Un puntero `CCreateContext` a la vista.

### <a name="return-value"></a>Valor devuelto

Un índice de vista si este método se realiza correctamente. En caso contrario, -1.

### <a name="remarks"></a>Observaciones

Llame a esta función para agregar una vista al control de ficha que está incrustado en un marco.

## <a name="ctabviewfindtab"></a><a name="findtab"></a>CTabView::FindTab

Devuelve el índice de la vista especificada en el control de ficha.

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>Parámetros

*hWndView*<br/>
[en] El identificador de la vista.

### <a name="return-value"></a>Valor devuelto

El índice de la vista si se encuentra; de lo contrario, -1.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar el índice de una vista que tiene un identificador especificado.

## <a name="ctabviewgetactiveview"></a><a name="getactiveview"></a>CTabView::GetActiveView

Devuelve un puntero a la vista activa actualmente.

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero válido a la vista activa, o NULL si no hay ninguna vista activa.

### <a name="remarks"></a>Observaciones

## <a name="ctabviewgettabcontrol"></a><a name="gettabcontrol"></a>CTabView::GetTabControl

Devuelve una referencia al control de ficha asociado a la vista.

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>Valor devuelto

Una referencia al control de ficha asociado a la vista.

## <a name="ctabviewisscrollbar"></a><a name="isscrollbar"></a>CTabView::IsScrollBar

Llamado por el marco de trabajo al crear una vista de ficha para determinar si la vista de ficha tiene una barra de desplazamiento horizontal compartida.

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la vista de pestaña debe crearse junto con una barra de desplazamiento compartida. De lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando se crea un *CTabView* objeto.

Invalidar el *IsScrollBar* método en un *CTabView*-clase derivada y devolver TRUE si desea crear una vista que tiene una barra de desplazamiento horizontal compartida.

## <a name="ctabviewonactivateview"></a><a name="onactivateview"></a>CTabView::OnActivateView

Llamado por el marco de trabajo cuando la vista de ficha se activa o inactiva.

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>Parámetros

*Vista*<br/>
[en] Un puntero a la vista.

### <a name="remarks"></a>Observaciones

La implementación predeterminada no hace nada. Invalide este `CTabView`método en una clase derivada para procesar esta notificación.

## <a name="ctabviewremoveview"></a><a name="removeview"></a>CTabView::RemoveView

Quita la vista del control de ficha.

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>Parámetros

*iTabNum*<br/>
[en] El índice de la vista que se va a quitar.

### <a name="return-value"></a>Valor devuelto

El índice de la vista quitada si este método se realiza correctamente. De lo contrario -1.

### <a name="remarks"></a>Observaciones

## <a name="ctabviewsetactiveview"></a><a name="setactiveview"></a>CTabView::SetActiveView

Activa una vista.

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>Parámetros

*iTabNum*<br/>
[en] El índice de base cero de la vista de ficha.

### <a name="return-value"></a>Valor devuelto

TRUESi la vista especificada se ha puesto activa, FALSE si el índice de la vista no es válido.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)
