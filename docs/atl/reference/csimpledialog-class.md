---
title: Clase CSimpleDialog
ms.date: 11/04/2016
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
ms.openlocfilehash: 345372d71ad96a74bb0ae6dd7e89bdf0724cd822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330832"
---
# <a name="csimpledialog-class"></a>Clase CSimpleDialog

Esta clase implementa un cuadro de diálogo modal básico.

## <a name="syntax"></a>Sintaxis

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>Parámetros

*t_wDlgTemplateID*

El identificador de recurso del recurso de plantilla de cuadro de diálogo.

*t_bCenter*<br/>
TRUESi el objeto de cuadro de diálogo debe centrarse en la ventana propietaria; de lo contrario FALSO.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleDialog::DoModal](#domodal)|Crea un cuadro de diálogo modal.|

## <a name="remarks"></a>Observaciones

Implementa un cuadro de diálogo modal con funcionalidad básica. `CSimpleDialog`proporciona compatibilidad solo con controles comunes de Windows. Para crear y mostrar un cuadro de diálogo modal, cree una instancia de esta clase, proporcionando el nombre de una plantilla de recursos existente para el cuadro de diálogo. El objeto de cuadro de diálogo se cierra cuando el usuario hace clic en cualquier control con un valor predefinido (como IDOK o IDCANCEL).

`CSimpleDialog`le permite crear solo cuadros de diálogo modales. `CSimpleDialog`proporciona el procedimiento de cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para dirigir los mensajes a los controladores adecuados.

Consulte [Implementación de un cuadro de diálogo](../../atl/implementing-a-dialog-box.md) para obtener más información.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="csimpledialogdomodal"></a><a name="domodal"></a>CSimpleDialog::DoModal

Invoca un cuadro de diálogo modal y devuelve el resultado del cuadro de diálogo cuando se hace.

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
Identificador del elemento primario del cuadro de diálogo. Si no se proporciona ningún valor, el elemento primario se establece en la ventana activa actual.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el valor devuelto es el identificador de recurso del control que descartó el cuadro de diálogo.

Si se produce un error en la función, el valor devuelto es -1. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

### <a name="remarks"></a>Observaciones

Este método controla toda la interacción con el usuario mientras el cuadro de diálogo está activo. Esto es lo que hace que el cuadro de diálogo sea modal; es decir, el usuario no puede interactuar con otras ventanas hasta que se cierra el cuadro de diálogo.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
