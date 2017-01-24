---
title: "CSnapInPropertyPageImpl Class | Microsoft Docs"
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
  - "CSnapInPropertyPageImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSnapInPropertyPageImpl class"
  - "páginas de propiedades, ATL"
  - "snap-ins"
  - "snap-ins, páginas de propiedades"
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSnapInPropertyPageImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para implementar un objeto de la página de propiedades del complemento.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
CSnapInPropertyPageImpl : public CDialogImplBase  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](../Topic/CSnapInPropertyPageImpl::CSnapInPropertyPageImpl.md)|Constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CancelToClose](../Topic/CSnapInPropertyPageImpl::CancelToClose.md)|cambia el estado de los botones de **Aceptar** y de **Cancelar** .|  
|[CSnapInPropertyPageImpl::Create](../Topic/CSnapInPropertyPageImpl::Create.md)|Inicializa un objeto creado recientemente de `CSnapInPropertyPageImpl` .|  
|[CSnapInPropertyPageImpl::OnApply](../Topic/CSnapInPropertyPageImpl::OnApply.md)|Llamado por el marco cuando el usuario hace clic en el botón de **Aplicar ahora** mientras utiliza una hoja de propiedades de asistente\-tipo.|  
|[CSnapInPropertyPageImpl::OnHelp](../Topic/CSnapInPropertyPageImpl::OnHelp.md)|Llamado por el marco cuando el usuario hace clic en el botón de **Ayuda** mientras utiliza una hoja de propiedades de asistente\-tipo.|  
|[CSnapInPropertyPageImpl::OnKillActive](../Topic/CSnapInPropertyPageImpl::OnKillActive.md)|Llamado por el marco cuando la página actual no esté activa.|  
|[CSnapInPropertyPageImpl::OnQueryCancel](../Topic/CSnapInPropertyPageImpl::OnQueryCancel.md)|Llamado por el marco cuando el usuario hace clic en el botón de **Cancelar** y antes de que ha ocurrido la cancelación.|  
|[CSnapInPropertyPageImpl::OnReset](../Topic/CSnapInPropertyPageImpl::OnReset.md)|Llamado por el marco cuando el usuario hace clic en el botón de **Restablecer** mientras utiliza una hoja de propiedades de asistente\-tipo.|  
|[CSnapInPropertyPageImpl::OnSetActive](../Topic/CSnapInPropertyPageImpl::OnSetActive.md)|Llamado por el marco cuando la página actual se activa.|  
|[CSnapInPropertyPageImpl::OnWizardBack](../Topic/CSnapInPropertyPageImpl::OnWizardBack.md)|Llamado por el marco cuando el usuario hace clic en el botón de**Atrás** mientras utiliza una hoja de propiedades de asistente\- tipo.|  
|[CSnapInPropertyPageImpl::OnWizardFinish](../Topic/CSnapInPropertyPageImpl::OnWizardFinish.md)|Llamado por el marco cuando el usuario hace clic en el botón de **Finalizar** mientras utiliza una hoja de propiedades de asistente\-tipo.|  
|[CSnapInPropertyPageImpl::OnWizardNext](../Topic/CSnapInPropertyPageImpl::OnWizardNext.md)|Llamado por el marco cuando el usuario hace clic en el botón de `Next` mientras utiliza una hoja de propiedades de asistente\-tipo.|  
|[CSnapInPropertyPageImpl::QuerySiblings](../Topic/CSnapInPropertyPageImpl::QuerySiblings.md)|Transmite el mensaje actual todas las páginas de la hoja de propiedades.|  
|[CSnapInPropertyPageImpl::SetModified](../Topic/CSnapInPropertyPageImpl::SetModified.md)|Llame a para activar o desactivar el botón de **Aplicar ahora** .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::m\_psp](../Topic/CSnapInPropertyPageImpl::m_psp.md)|la estructura de Windows **PROPSHEETPAGE** utilizada por el objeto de `CSnapInPropertyPageImpl` .|  
  
## Comentarios  
 `CSnapInPropertyPageImpl` proporciona una implementación básica de un objeto de la página de propiedades del complemento.  Las características básicas de la página de propiedades de complemento se implementan utilizando varias diferentes interfaces y tipos de mapa.  
  
## Jerarquía de herencia  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## Requisitos  
 **encabezado:** atlsnap.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)