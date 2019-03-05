---
title: CSimpleDialog (clase)
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
ms.openlocfilehash: b0790d9c29b50b1ac454815cd2189e0efb31b9ef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293549"
---
# <a name="csimpledialog-class"></a>CSimpleDialog (clase)

Esta clase implementa un cuadro de diálogo modal básica.

## <a name="syntax"></a>Sintaxis

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>Parámetros

*t_wDlgTemplateID*

El identificador de recurso del recurso de plantilla de cuadro de diálogo.

*t_bCenter*<br/>
Es TRUE si el objeto de cuadro de diálogo se centra en la ventana propietaria; en caso contrario, FALSE.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleDialog::DoModal](#domodal)|Crea un cuadro de diálogo modal.|

## <a name="remarks"></a>Comentarios

Implementa un cuadro de diálogo modal con funcionalidad básica. `CSimpleDialog` proporciona compatibilidad para controles comunes de Windows. Para crear y mostrar un cuadro de diálogo modal, cree una instancia de esta clase, proporcionando el nombre de una plantilla de recursos existente para el cuadro de diálogo. El objeto de cuadro de diálogo se cierra cuando el usuario hace clic en cualquier control con un valor predefinido (por ejemplo, IDOK o IDCANCEL).

`CSimpleDialog` le permite crear sólo los cuadros de diálogo modales. `CSimpleDialog` proporciona el procedimiento de cuadro de diálogo, que usa el mapa de mensajes predeterminado para dirigir mensajes a los controladores adecuados.

Consulte [implementa un cuadro de diálogo](../../atl/implementing-a-dialog-box.md) para obtener más información.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="domodal"></a>  CSimpleDialog::DoModal

Invoca un cuadro de diálogo modal y devuelve el resultado del cuadro de diálogo cuando haya terminado.

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
Un identificador para el elemento primario del cuadro de diálogo. Si se proporciona ningún valor, el elemento primario se establece en la ventana activa actual.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el valor devuelto es el identificador de recurso del control que se cierra el cuadro de diálogo.

Si se produce un error en la función, el valor devuelto es -1. Para obtener información de errores extendida, realice una llamada a `GetLastError`.

### <a name="remarks"></a>Comentarios

Este método controla toda la interacción con el usuario mientras el cuadro de diálogo está activo. Esto es lo que hace que el cuadro de diálogo modal; es decir, el usuario no puede interactuar con otras ventanas hasta que se cierre el cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
