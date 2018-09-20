---
title: CWinFormsView (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4d90f2a7f964d264966d5254d051ebddaf2baa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448147"
---
# <a name="cwinformsview-class"></a>CWinFormsView (clase)

Proporciona funcionalidad genérica para hospedar un control de formularios Windows Forms como vista MFC.

## <a name="syntax"></a>Sintaxis

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|Construye un objeto `CWinFormsView`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[:: GetControl](#getcontrol)|Recupera un puntero al control de Windows Forms.|

### <a name="public-operators"></a>Operadores públicos

|nombre||
|----------|-|
|[Control CWinFormsView::operator ^](#operator_control)|Convierte un tipo de puntero a un control de Windows Forms.|

## <a name="remarks"></a>Comentarios

MFC utiliza el `CWinFormsView` clase para hospedar un control de Windows Forms de .NET Framework dentro de una vista MFC. El control es un elemento secundario de la vista nativa y ocupa toda el área cliente de la vista MFC. El resultado es similar a un `CFormView` vista, lo que permite aprovechar las ventajas del Diseñador de Windows Forms y tiempo de ejecución para crear vistas enriquecidas basadas en formularios.

Para obtener más información sobre el uso de Windows Forms, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
>  Integración de formularios Windows Forms de MFC sólo funciona en los proyectos que se vinculan dinámicamente con MFC (proyectos en el que se ha definido AFXDLL).

> [!NOTE]
>  CWinFormsView no es compatible con la ventana divisora MFC ( [CSplitterWnd (clase)](../../mfc/reference/csplitterwnd-class.md)). Actualmente sólo Windows Forms divisor se admite el control.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h

##  <a name="cwinformsview"></a>  CWinFormsView::CWinFormsView

Construye un objeto `CWinFormsView`.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parámetros

*pManagedViewType*<br/>
Un puntero al tipo de datos del control de usuario de Windows Forms.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente, la `CUserView` clase hereda de `CWinFormsView` y pasa el tipo de `UserControl1` a la `CWinFormsView` constructor. `UserControl1` es un control personalizado en ControlLibrary1.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>  :: GetControl

Recupera un puntero al control de Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un `System.Windows.Forms.Control` objeto.

### <a name="remarks"></a>Comentarios

Para obtener un ejemplo de cómo usar Windows Forms, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_control"></a>  Control CWinFormsView::operator ^

Convierte un tipo de puntero a un control de Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Comentarios

Este operador permite pasar un `CWinFormsView` vista a las funciones que aceptan un puntero a un control Windows Forms del tipo <xref:System.Windows.Forms.Control>.

### <a name="example"></a>Ejemplo

  Consulte [:: GetControl](#getcontrol).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl (clase)](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog (clase)](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView (clase)](../../mfc/reference/cformview-class.md)
