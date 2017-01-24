---
title: "CSimpleDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CSimpleDialog"
  - "CSimpleDialgo"
  - "CSimpleDialog"
  - "ATL.CSimpleDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleDialog class"
  - "CSimpleDialog class, modal dialog boxes in ATL"
  - "cuadros de diálogo, modales"
  - "cuadros de diálogo modales, ATL"
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa un cuadro de diálogo modal básico.  
  
## Sintaxis  
  
```  
  
      template <  
   WORD t_wDlgTemplateID,  
   BOOL t_bCenter = TRUE  
>  
class CSimpleDialog :  
   public CDialogImplBase  
```  
  
#### Parámetros  
 *t\_wDlgTemplateID*  
  
 El Id. de recurso de plantilla de cuadro de diálogo.  
  
 *t\_bCenter*  
 **TRUE** si el objeto de diálogo a estar centrado en la ventana propietaria; si no **FALSE**.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleDialog::DoModal](../Topic/CSimpleDialog::DoModal.md)|crea un cuadro de diálogo modal.|  
  
## Comentarios  
 Implementa un cuadro de diálogo modal con funcionalidad básica.  `CSimpleDialog` proporciona compatibilidad para controles comunes de Windows sólo.  Para crear y mostrar un cuadro de diálogo modal, cree una instancia de esta clase, proporcionando el nombre de una plantilla existente de recursos para el cuadro de diálogo.  El objeto de cuadro de diálogo se cierra cuando el usuario hace clic en cualquier control con un valor predefinido \(como IDOK o IDCANCEL\).  
  
 `CSimpleDialog` permite crear sólo los cuadros de diálogo modales.  `CSimpleDialog` proporciona el procedimiento del cuadro de diálogo, que utiliza el mapa de mensajes predeterminado para enviar mensajes a los controladores adecuados.  
  
 Vea [implementar un cuadro de diálogo](../../atl/implementing-a-dialog-box.md) para obtener más información.  
  
## Jerarquía de herencia  
 `CDialogImplBase`  
  
 `CSimpleDialog`  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)