---
title: CMFCRibbonCustomizePropertyPage (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
ms.openlocfilehash: c77e2fed1067091c139eee664fb291b83742eb54
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375197"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage (clase)

Implementa una página personalizada para el cuadro de diálogo **Personalizar** en aplicaciones basadas en cinta de opciones.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Construye un objeto `CMFCRibbonCustomizePropertyPage`.|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Agrega una categoría personalizada al cuadro combinado **Comandos.**|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Llamado por el sistema cuando un usuario hace clic en **Aceptar** en el cuadro de diálogo **Personalizar.**|

## <a name="remarks"></a>Observaciones

Si desea agregar comandos personalizados al cuadro de diálogo **Personalizar,** debe controlar el mensaje de AFX_WM_ON_RIBBON_CUSTOMIZE. En el controlador de `CMFCRibbonCustomizePropertyPage` mensajes, cree una instancia de un objeto en la pila. Cree una lista de comandos `AddCustomCategory` personalizados y, a continuación, llame para agregar la nueva página al cuadro de diálogo **Personalizar.**

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCRibbonCustomizePropertyPage` muestra cómo construir un objeto y agregar una categoría personalizada.

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribboncustomizedialog.h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a>CMFCRibbonCustomizePropertyPage::AddCustomCategory

Agrega una categoría personalizada al cuadro combinado **Comandos.**

```
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*lpszName*|[en] Especifica el nombre de categoría personalizado.|
|*lstIDS*|[en] Contiene los ides de comando de la cinta de opciones que se mostrarán en la categoría personalizada.|

### <a name="remarks"></a>Observaciones

Este método agrega una categoría denominada *lpszName* al cuadro combinado **Comandos.** Cuando el usuario selecciona la categoría, los comandos especificados en *lstIDS* aparecen en la lista de comandos.

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a>CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

Construye un objeto `CMFCRibbonCustomizePropertyPage`.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>Parámetros

*pRibbonBar*<br/>
[en] Puntero a un control de cinta de opciones para el que se pueden personalizar las opciones.

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a>CMFCRibbonCustomizePropertyPage::OnOK

Calleld por el sistema cuando un usuario hace clic en **Aceptar** en el cuadro de diálogo **Personalizar.**

```
virtual void OnOK();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada aplica las opciones seleccionadas en el cuadro de diálogo **Personalizar** a la barra de herramientas de acceso rápido.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
