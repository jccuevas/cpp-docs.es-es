---
title: IView (interfaz)
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: dfe77699a51ad2670c703d02e13e9062e76debcd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751281"
---
# <a name="iview-interface"></a>IView (interfaz)

Implementa varios métodos que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utiliza para enviar notificaciones de vista a un control administrado.

## <a name="syntax"></a>Sintaxis

```
interface class IView
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IView::OnActivateView](#onactivateview)|Llamado por MFC cuando se activa o desactiva una vista.|
|[IView::OnInitialUpdate](#oninitialupdate)|Llamado por el marco de trabajo después de que la vista se adjunta primero al documento, pero antes de que se muestre inicialmente la vista.|
|[IView::OnUpdate](#onupdate)|Llamado por MFC después de que se ha modificado el documento de la vista; esta función permite a la vista actualizar su visualización para reflejar las modificaciones.|

## <a name="remarks"></a>Observaciones

`IView`implementa varios métodos que `CWinFormsView` se usan para reenviar notificaciones de vista comunes a un control administrado hospedado. Se trata de [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) y [OnActivateView](#onactivateview).

`IView`es similar a [CView](../../mfc/reference/cview-class.md), pero solo se utiliza con vistas y controles administrados.

Para obtener más información sobre el uso de formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Requisitos

Encabezado: afxwinforms.h (definido en el ensamblado atlmfc-lib-mfcmifc80.dll)

## <a name="iviewonactivateview"></a><a name="onactivateview"></a>IView::OnActivateView

Llamado por MFC cuando se activa o desactiva una vista.

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parámetros

*activar*<br/>
Indica si la vista se está activando o desactivando.

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a>IView::OnInitialUpdate

Llamado por el marco de trabajo después de que la vista se adjunta primero al documento, pero antes de que se muestre inicialmente la vista.

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a>IView::OnUpdate

Llamado por MFC después de que se ha modificado el documento de la vista.

```cpp
void OnUpdate();
```

## <a name="remarks"></a>Observaciones

Esta función permite a la vista actualizar su visualización para reflejar las modificaciones.

## <a name="see-also"></a>Vea también

[CWinFormsView (clase)](../../mfc/reference/cwinformsview-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)
