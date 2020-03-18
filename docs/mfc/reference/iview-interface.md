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
ms.openlocfilehash: 22e08a70ff4cc742406a1489899c0ba1df7eb664
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426256"
---
# <a name="iview-interface"></a>IView (interfaz)

Implementa varios métodos que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) usa para enviar notificaciones de vista a un control administrado.

## <a name="syntax"></a>Sintaxis

```
interface class IView
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IView:: OnActivateView](#onactivateview)|Lo llama MFC cuando una vista está activada o desactivada.|
|[IView:: OnInitialUpdate](#oninitialupdate)|Lo llama el marco de trabajo después de adjuntar la vista por primera vez al documento, pero antes de que se muestre inicialmente la vista.|
|[IView:: actualización](#onupdate)|Llamado por MFC después de modificar el documento de la vista; Esta función permite que la vista actualice su presentación para reflejar las modificaciones.|

## <a name="remarks"></a>Observaciones

`IView` implementa varios métodos que `CWinFormsView` utiliza para reenviar las notificaciones de vista comunes a un control administrado hospedado. Son [OnInitialUpdate](#oninitialupdate), [ALUpdate](#onupdate) y [OnActivateView](#onactivateview).

`IView` es similar a [CView](../../mfc/reference/cview-class.md), pero solo se usa con vistas y controles administrados.

Para obtener más información sobre el uso de Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Requisitos

Encabezado: afxwinforms. h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)

## <a name="onactivateview"></a>IView:: OnActivateView

Lo llama MFC cuando una vista está activada o desactivada.
```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parámetros

*activar*<br/>
Indica si la vista se está activando o desactivando.

## <a name="oninitialupdate"></a>IView:: OnInitialUpdate

Lo llama el marco de trabajo después de adjuntar la vista por primera vez al documento, pero antes de que se muestre inicialmente la vista.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a>IView:: actualización

Lo llama MFC después de modificar el documento de la vista.
```
void OnUpdate();
```

## <a name="remarks"></a>Observaciones

Esta función permite que la vista actualice su presentación para reflejar las modificaciones.

## <a name="see-also"></a>Consulte también

[CWinFormsView (clase)](../../mfc/reference/cwinformsview-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)
