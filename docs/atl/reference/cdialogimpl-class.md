---
title: "CDialogImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDialogImpl"
  - "ATL.CDialogImpl"
  - "ATL::CDialogImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialogImpl class"
  - "cuadros de diálogo, ATL"
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
caps.latest.revision: 25
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDialogImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para crear un cuadro de diálogo modal o no modal.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class T,  
class TBase= CWindow   
>  
class ATL_NO_VTABLE CDialogImpl :  
public CDialogImplBaseT< TBase>  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `CDialogImpl`.  
  
 *TBase*  
 la clase base de la nueva clase.  la clase base predeterminada es [CWindow](../../atl/reference/cwindow-class.md).  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[Creación](../Topic/CDialogImpl::Create.md)|Crea un cuadro de diálogo no modal.|  
|[DestroyWindow](../Topic/CDialogImpl::DestroyWindow.md)|Destruye un cuadro de diálogo no modal.|  
|[DoModal](../Topic/CDialogImpl::DoModal.md)|crea un cuadro de diálogo modal.|  
|[EndDialog](../Topic/CDialogImpl::EndDialog.md)|destruye un cuadro de diálogo modal.|  
  
### métodos de CDialogImplBaseT  
  
|||  
|-|-|  
|[GetDialogProc](../Topic/CDialogImpl::GetDialogProc.md)|Devuelve el procedimiento de cuadro de diálogo actual.|  
|[MapDialogRect](../Topic/CDialogImpl::MapDialogRect.md)|Asigna las unidades de cuadro de diálogo del rectángulo especificado a unidades de pantalla \(píxeles\).|  
|[OnFinalMessage](../Topic/CDialogImpl::OnFinalMessage.md)|Se llama después de recibir el mensaje pasado, normalmente `WM_NCDESTROY`.|  
  
### Funciones de estático  
  
|||  
|-|-|  
|[DialogProc](../Topic/CDialogImpl::DialogProc.md)|Procesa mensajes enviados al cuadro de diálogo.|  
|[StartDialogProc](../Topic/CDialogImpl::StartDialogProc.md)|Se llama cuando el primer mensaje se recibe para procesar los mensajes enviados al cuadro de diálogo.|  
  
## Comentarios  
 Con `CDialogImpl` puede crear un cuadro de diálogo modal o no modal.  `CDialogImpl` proporciona el procedimiento del cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para enviar mensajes a los controladores adecuados.  
  
 La clase base destructor **~CWindowImplRoot** garantiza que la ventana se ida antes de destruir el objeto.  
  
 `CDialogImpl` deriva de **CDialogImplBaseT**, que a su vez deriva de **CWindowImplRoot**.  
  
> [!NOTE]
>  La clase debe definir un miembro de **IDD** que especifica el identificador de recurso de plantilla de cuadro de diálogo  Por ejemplo, el asistente para proyectos ATL agrega automáticamente la línea siguiente a la clase:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/CPP/cdialogimpl-class_1.h)]  
  
 donde es **nombre corto**`MyDlg` escrito en la página de **nombres** del asistente.  
  
|Para obtener más información sobre|Vea|  
|----------------------------------------|---------|  
|Crear controles|[tutorial de ATL](../../atl/active-template-library-atl-tutorial.md)|  
|Mediante cuadros de diálogo en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|  
|Asistente para proyectos ATL|[Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|  
|Cuadros de diálogo|[cuadros de diálogo](http://msdn.microsoft.com/library/windows/desktop/ms632588) y los temas siguientes en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)