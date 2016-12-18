---
title: "CMenuTearOffManager Class | Microsoft Docs"
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
  - "CMenuTearOffManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMenuTearOffManager class"
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
caps.latest.revision: 31
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMenuTearOffManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

manages rasga menús.  Un menú de rasgón es un menú de la barra de menús.  El usuario puede quitar un menú de rasgón de barra de menús, produciendo el menú de rasgón a float.  
  
## Sintaxis  
  
```  
class CMenuTearOffManager : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMenuTearOffManager::CMenuTearOffManager](../Topic/CMenuTearOffManager::CMenuTearOffManager.md)|Crea un objeto `CMenuTearOffManager`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMenuTearOffManager::Build](../Topic/CMenuTearOffManager::Build.md)||  
|[CMenuTearOffManager::GetRegPath](../Topic/CMenuTearOffManager::GetRegPath.md)||  
|[CMenuTearOffManager::Initialize](../Topic/CMenuTearOffManager::Initialize.md)|Inicializa un objeto de `CMenuTearOffManager` .|  
|[CMenuTearOffManager::IsDynamicID](../Topic/CMenuTearOffManager::IsDynamicID.md)||  
|[CMenuTearOffManager::Parse](../Topic/CMenuTearOffManager::Parse.md)||  
|[CMenuTearOffManager::Reset](../Topic/CMenuTearOffManager::Reset.md)||  
|[CMenuTearOffManager::SetInUse](../Topic/CMenuTearOffManager::SetInUse.md)||  
|[CMenuTearOffManager::SetupTearOffMenus](../Topic/CMenuTearOffManager::SetupTearOffMenus.md)||  
  
## Comentarios  
 Para utilizar rasgue menús en la aplicación, debe tener un objeto de `CMenuTearOffManager` .  En la mayoría de los casos, no creará ni se inicializará un objeto de `CMenuTearOffManager` directamente.  Esto se administra al llamar a la función de [CWinAppEx::EnableTearOffMenus](../Topic/CWinAppEx::EnableTearOffMenus.md) .  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo crear e inicializar un objeto de `CMenuTearOffManager` llamando al método de `CWinAppEX::EnableTearOffMenus` .  Este fragmento de código es parte de [Ejemplo de pista de word](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/CPP/cmenutearoffmanager-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)  
  
## Requisitos  
 **encabezado:** afxmenutearoffmanager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)