---
title: CSimpleDialog (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3a8f6cb2ead8798b86d65a1fa875a42a68cdd77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362392"
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
  
 *t_bCenter*  
 **TRUE** si el objeto de cuadro de diálogo está centrado en la ventana propietaria; en caso contrario **FALSE**.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleDialog::DoModal](#domodal)|Crea un cuadro de diálogo modal.|  
  
## <a name="remarks"></a>Comentarios  
 Implementa un cuadro de diálogo modal con funcionalidad básica. `CSimpleDialog` proporciona compatibilidad para controles comunes de Windows. Para crear y mostrar un cuadro de diálogo modal, cree una instancia de esta clase, proporcionando el nombre de una plantilla de recursos existente para el cuadro de diálogo. El objeto de cuadro de diálogo se cierra cuando el usuario hace clic en cualquier control con un valor predefinido (por ejemplo, IDOK o IDCANCEL).  
  
 `CSimpleDialog` le permite crear cuadros de diálogo modales solo. `CSimpleDialog` proporciona el procedimiento de cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para dirigir mensajes a los controladores adecuados.  
  
 Vea [implementa un cuadro de diálogo](../../atl/implementing-a-dialog-box.md) para obtener más información.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CDialogImplBase`  
  
 `CSimpleDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="domodal"></a>  CSimpleDialog::DoModal  
 Invoca un cuadro de diálogo modal y devuelve el resultado de cuadro de diálogo cuando haya finalizado.  
  
```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 Un identificador para el elemento primario del cuadro de diálogo. Si no se proporciona ningún valor, se establece el elemento primario en la ventana activa actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el valor devuelto es el identificador de recurso del control que cierra el cuadro de diálogo.  
  
 Si se produce un error en la función, el valor devuelto es -1. Para obtener información de errores extendida, realice una llamada a `GetLastError`.  
  
### <a name="remarks"></a>Comentarios  
 Este método controla toda la interacción con el usuario mientras el cuadro de diálogo está activo. Esto es lo que hace que el cuadro de diálogo modal; es decir, el usuario no puede interactuar con otras ventanas hasta que se cierra el cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
