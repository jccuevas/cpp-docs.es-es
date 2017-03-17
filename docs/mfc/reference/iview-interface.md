---
title: Interfaz IView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IView
- No header/IView
- No header/IView::OnActivateView
- No header/IView::OnInitialUpdate
- No header/IView::OnUpdate
dev_langs:
- C++
helpviewer_keywords:
- views [MFC]
- IView class
- views, classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 9a8b5f2d9d123aa3032cb30ecdbdd1cd380b32f8
ms.lasthandoff: 02/24/2017

---
# <a name="iview-interface"></a>Interfaz IView
Implementa varios métodos que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utiliza para enviar notificaciones de vista para un control administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
interface class IView  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IView::OnActivateView](#onactivateview)|Llamado por MFC cuando una vista está activada o desactivada.|  
|[IView:: OnInitialUpdate](#oninitialupdate)|Lo llama el marco de trabajo después de la vista se adjunta al documento en primer lugar, pero antes de que la vista se muestra inicialmente.|  
|[IView::OnUpdate](#onupdate)|MFC llama después de que se ha modificado el documento de la vista; Esta función permite que la vista actualice su presentación para reflejar las modificaciones.|  
  
## <a name="remarks"></a>Comentarios  
 `IView`implementa varios métodos que `CWinFormsView` usa para reenviar las notificaciones de vistas comunes para un control administrado hospedado. Estos son [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) y [OnActivateView](#onactivateview).  
  
 `IView`es similar a [CView](../../mfc/reference/cview-class.md), pero sólo se utiliza con vistas administradas y controles.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  

## <a name="requirements"></a>Requisitos  
 Encabezado: afxwinforms.h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)  

## <a name="onactivateview"></a>IView::OnActivateView  
Llamado por MFC cuando una vista está activada o desactivada.
```
void OnActivateView(bool activate);
```
## <a name="parameters"></a>Parámetros
`activate`  
Indica si la vista se activa o se desactiva.  

## <a name="oninitialupdate"></a>IView:: OnInitialUpdate
Lo llama el marco de trabajo después de la vista se adjunta al documento en primer lugar, pero antes de que la vista se muestra inicialmente.
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

