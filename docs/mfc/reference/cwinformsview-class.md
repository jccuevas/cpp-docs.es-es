---
title: CWinFormsView (clase)
ms.date: 11/04/2016
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
ms.openlocfilehash: 6eb6b9e385e9dbc96eb3b62ffb80909e54569e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369607"
---
# <a name="cwinformsview-class"></a>CWinFormsView (clase)

Proporciona funcionalidad genérica para hospedar un control de formularios Windows Forms como vista MFC.

## <a name="syntax"></a>Sintaxis

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|Construye un objeto `CWinFormsView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinFormsView::GetControl](#getcontrol)|Recupera un puntero al control de formularios Windows Forms.|

### <a name="public-operators"></a>Operadores públicos

|Nombre||
|----------|-|
|[CWinFormsView::operador Control](#operator_control)|Convierte un tipo como un puntero a un control de formularios Windows Forms.|

## <a name="remarks"></a>Observaciones

MFC usa `CWinFormsView` la clase para hospedar un control de formularios Windows Forms de .NET Framework dentro de una vista MFC. El control es un elemento secundario de la vista nativa y ocupa todo el área de cliente de la vista MFC. El resultado es `CFormView` similar a una vista, lo que le permite aprovechar el diseñador de Windows Forms y el tiempo de ejecución para crear vistas basadas en formularios enriquecidos.

Para obtener más información sobre el uso de formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
> La integración de formularios Windows Forms de MFC solo funciona en proyectos que se vinculan dinámicamente con MFC (proyectos en los que se define AFXDLL).

> [!NOTE]
> CWinFormsView no admite la ventana divisora MFC ( [CSplitterWnd (Clase)](../../mfc/reference/csplitterwnd-class.md)). Actualmente solo se admite el control Splitter de formularios Windows Forms.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h

## <a name="cwinformsviewcwinformsview"></a><a name="cwinformsview"></a>CWinFormsView::CWinFormsView

Construye un objeto `CWinFormsView`.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parámetros

*pManagedViewType*<br/>
Puntero al tipo de datos del control de usuario de formularios Windows Forms.

### <a name="example"></a>Ejemplo

En el ejemplo `CUserView` siguiente, la `CWinFormsView` clase hereda `UserControl1` y `CWinFormsView` pasa el tipo de al constructor. `UserControl1`es un control personalizado en ControlLibrary1.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

## <a name="cwinformsviewgetcontrol"></a><a name="getcontrol"></a>CWinFormsView::GetControl

Recupera un puntero al control de formularios Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `System.Windows.Forms.Control` .

### <a name="remarks"></a>Observaciones

Para obtener un ejemplo de cómo usar formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsviewoperator-control"></a><a name="operator_control"></a>CWinFormsView::operador Control

Convierte un tipo como un puntero a un control de formularios Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Observaciones

Este operador permite pasar `CWinFormsView` una vista a funciones que aceptan <xref:System.Windows.Forms.Control>un puntero a un control de formularios Windows Forms de tipo .

### <a name="example"></a>Ejemplo

  Vea [CWinFormsView::GetControl](#getcontrol).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl (clase)](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog (clase)](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Clase CFormView](../../mfc/reference/cformview-class.md)
