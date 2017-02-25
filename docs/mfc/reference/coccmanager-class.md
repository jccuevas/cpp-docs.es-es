---
title: "COccManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COccManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores de controles ActiveX [C++], control site"
  - "CNoTrackObject class"
  - "COccManager class"
  - "controles personalizados [MFC], sites"
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# COccManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Administra distintos sitios de control personalizado; implementado por `COleControlContainer` y los objetos de `COleControlSite` .  
  
## Sintaxis  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COccManager::CreateContainer](../Topic/COccManager::CreateContainer.md)|crea un objeto de **COleContainer** .|  
|[COccManager::CreateDlgControls](../Topic/COccManager::CreateDlgControls.md)|Crea los controles ActiveX, hospedados por el objeto asociado de `COleContainer` .|  
|[COccManager::CreateSite](../Topic/COccManager::CreateSite.md)|Crea un objeto `COleClientSite`.|  
|[COccManager::GetDefBtnCode](../Topic/COccManager::GetDefBtnCode.md)|Recupera el código del botón predeterminado.|  
|[COccManager::IsDialogMessage](../Topic/COccManager::IsDialogMessage.md)|determina el destino de un mensaje de diálogo.|  
|[COccManager::IsLabelControl](../Topic/COccManager::IsLabelControl.md)|determina si el control especificado es un control de etiqueta.|  
|[COccManager::IsMatchingMnemonic](../Topic/COccManager::IsMatchingMnemonic.md)|Determina si coincide con la tecla de acceso actual la tecla de acceso del control especificado.|  
|[COccManager::OnEvent](../Topic/COccManager::OnEvent.md)|Intentos de controlar el evento especificado.|  
|[COccManager::PostCreateDialog](../Topic/COccManager::PostCreateDialog.md)|Libera los recursos asignados durante la creación del diálogo.|  
|[COccManager::PreCreateDialog](../Topic/COccManager::PreCreateDialog.md)|Procesa una plantilla de cuadro de diálogo para controles ActiveX.|  
|[COccManager::SetDefaultButton](../Topic/COccManager::SetDefaultButton.md)|Alterna el estado de control predeterminada especificado.|  
|[COccManager::SplitDialogTemplate](../Topic/COccManager::SplitDialogTemplate.md)|Separa cualquier control ActiveX existente de controles comunes en la plantilla especificada del diálogo.|  
  
## Comentarios  
 La clase base, **CNoTrackObject**, es una clase base indocumentada \(ubicada en AFXTLS.H\).  Diseñado para uso del marco de trabajo de MFC, las clases derivadas de la clase de **CNoTrackObject** no se aplica de la detección de pérdidas de memoria.  No se recomienda derivar directamente de **CNoTrackObject**.  
  
## Jerarquía de herencia  
 `CNoTrackObject`  
  
 `COccManager`  
  
## Requisitos  
 **encabezado:** afxocc.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleControlSite Class](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer Class](../../mfc/reference/colecontrolcontainer-class.md)