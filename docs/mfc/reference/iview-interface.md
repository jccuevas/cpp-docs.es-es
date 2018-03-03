---
title: Interfaz de IView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
dev_langs:
- C++
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4266d8f5ec564dac67d7167c6c9bab4768a0276
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="iview-interface"></a>Interfaz de IView
Implementa varios métodos que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utiliza para enviar notificaciones de vista para un control administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
interface class IView  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IView::OnActivateView](#onactivateview)|Llamado por MFC cuando se activa o desactiva una vista.|  
|[IView:: OnInitialUpdate](#oninitialupdate)|Lo llama el marco de trabajo después de la vista se adjunta al documento en primer lugar, pero antes de la vista se muestra inicialmente.|  
|[IView::OnUpdate](#onupdate)|Es llamado por MFC cuando se ha modificado el documento de la vista; Esta función permite que la vista actualice su presentación para reflejar las modificaciones.|  
  
## <a name="remarks"></a>Comentarios  
 `IView`implementa varios métodos que `CWinFormsView` usa para enviar notificaciones de vista comunes para un control hospedado administrado. Se trata de [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) y [OnActivateView](#onactivateview).  
  
 `IView`es similar a [CView](../../mfc/reference/cview-class.md), pero solo se usa con vistas administradas y controles.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  

## <a name="requirements"></a>Requisitos  
 Encabezado: afxwinforms.h (definido en atlmfc\lib\mfcmifc80.dll ensamblado)  

## <a name="onactivateview"></a>IView::OnActivateView  
Llamado por MFC cuando se activa o desactiva una vista.
```
void OnActivateView(bool activate);
```
## <a name="parameters"></a>Parámetros
`activate`  
Indica si la vista se está activando o desactivando.  

## <a name="oninitialupdate"></a>IView:: OnInitialUpdate
Lo llama el marco de trabajo después de la vista se adjunta al documento en primer lugar, pero antes de la vista se muestra inicialmente.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a>IView::OnUpdate 
Llamado por MFC cuando se ha modificado el documento de la vista.  
```
void OnUpdate();
```
## <a name="remarks"></a>Comentarios  
Esta función permite que la vista actualice su presentación para reflejar las modificaciones.

## <a name="see-also"></a>Vea también  
 [Clase CWinFormsView](../../mfc/reference/cwinformsview-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)
