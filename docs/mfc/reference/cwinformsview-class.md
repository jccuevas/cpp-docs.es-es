---
title: Clase CWinFormsView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs: C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb68e906a06d18b41d97851d8d91717ac3dd78b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cwinformsview-class"></a>Clase CWinFormsView
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
|[:: GetControl](#getcontrol)|Recupera un puntero para el control de formularios Windows Forms.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|nombre||  
|----------|-|  
|[Control de CWinFormsView::operator ^](#operator_control)|Convierte un tipo de un puntero a un control de formularios Windows Forms.|  
  
## <a name="remarks"></a>Comentarios  
 MFC utiliza la `CWinFormsView` clase para hospedar un control de formularios Windows Forms de .NET Framework en una vista MFC. El control es un elemento secundario de la vista nativa y ocupa toda el área cliente de la vista MFC. El resultado es similar a un `CFormView` vista, lo que permite aprovechar las ventajas del Diseñador de Windows Forms y tiempo de ejecución para crear vistas basadas en formulario enriquecidas.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
> [!NOTE]
>  Integración de formularios Windows Forms de MFC funciona sólo en los proyectos que se vinculen dinámicamente a MFC (proyectos en el que se ha definido AFXDLL).  
  
> [!NOTE]
>  CWinFormsView no es compatible con la ventana divisora MFC ( [clase CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)). Actualmente solo el Windows Forms divisor se admite el control.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwinforms.h  
  
##  <a name="cwinformsview"></a>CWinFormsView::CWinFormsView  
 Construye un objeto `CWinFormsView`.  
  
```  
CWinFormsView(System::Type^ pManagedViewType);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pManagedViewType`  
 Un puntero al tipo de datos del control de usuario de formularios Windows Forms.   
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, la `CUserView` clase hereda de `CWinFormsView` y pasa el tipo de `UserControl1` a la `CWinFormsView` constructor. `UserControl1`es un control personalizado en ControlLibrary1.dll.  
  
 [!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]  
  
 [!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]  
  
##  <a name="getcontrol"></a>:: GetControl  
 Recupera un puntero para el control de formularios Windows Forms.  
  
```  
System::Windows::Forms::Control^ GetControl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `System.Windows.Forms.Control` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo de cómo usar Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_control"></a>Control de CWinFormsView::operator ^  
 Convierte un tipo de un puntero a un control de formularios Windows Forms.  
  
```  
operator System::Windows::Forms::Control^() const;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este operador permite pasar un `CWinFormsView` vista a las funciones que aceptan un puntero a un control de formularios Windows Forms de tipo <xref:System.Windows.Forms.Control>.  
  
### <a name="example"></a>Ejemplo  
  Vea [:: GetControl](#getcontrol).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)   
 [Clase CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView (clase)](../../mfc/reference/cformview-class.md)
