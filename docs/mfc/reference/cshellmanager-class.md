---
title: "CShellManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CShellManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CShellManager class"
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CShellManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa varios métodos que le permiten trabajar con punteros a listas de identificador \(PIDLs\).  
  
## Sintaxis  
  
```  
class CShellManager : public CObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CShellManager::CShellManager](../Topic/CShellManager::CShellManager.md)|Crea un objeto `CShellManager`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CShellManager::BrowseForFolder](../Topic/CShellManager::BrowseForFolder.md)|Muestra un cuadro de diálogo que permite al usuario seleccionar una carpeta de shell.|  
|[CShellManager::ConcatenateItem](../Topic/CShellManager::ConcatenateItem.md)|concatena dos PIDLs.|  
|[CShellManager::CopyItem](../Topic/CShellManager::CopyItem.md)|Crea un nuevo PIDL y copia el PIDL proporcionado al.|  
|[CShellManager::CreateItem](../Topic/CShellManager::CreateItem.md)|Crea un nuevo PIDL del tamaño especificado.|  
|[CShellManager::FreeItem](../Topic/CShellManager::FreeItem.md)|elimina el PIDL proporcionado.|  
|[CShellManager::GetItemCount](../Topic/CShellManager::GetItemCount.md)|Devuelve el número de elementos del PIDL proporcionado.|  
|[CShellManager::GetItemSize](../Topic/CShellManager::GetItemSize.md)|Devuelve el tamaño de PIDL proporcionado.|  
|[CShellManager::GetNextItem](../Topic/CShellManager::GetNextItem.md)|Devuelve el siguiente elemento de PIDL.|  
|[CShellManager::GetParentItem](../Topic/CShellManager::GetParentItem.md)|Recupera el elemento primario del elemento proporcionado.|  
|[CShellManager::ItemFromPath](../Topic/CShellManager::ItemFromPath.md)|Recupera el PIDL para el elemento identificado por la ruta de acceso proporcionada.|  
  
## Comentarios  
 los métodos de la clase de `CShellManager` todos tratan de PIDLs.  Un PIDL es un identificador único para un objeto de shell.  
  
 No debe crear un objeto de `CShellManager` manualmente.  Se creará automáticamente el marco de trabajo de la aplicación.  Sin embargo, debe llamar a [CWinAppEx::InitShellManager](../Topic/CWinAppEx::InitShellManager.md) durante el proceso de inicialización de la aplicación.  Para obtener un puntero al administrador shell para la aplicación, llame a [CWinAppEx::GetShellManager](../Topic/CWinAppEx::GetShellManager.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CShellManager](../../mfc/reference/cshellmanager-class.md)  
  
## Requisitos  
 **encabezado:** afxshellmanager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)