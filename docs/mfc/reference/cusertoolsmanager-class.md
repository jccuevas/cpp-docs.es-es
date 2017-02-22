---
title: "CUserToolsManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CUserToolsManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUserToolsManager class"
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CUserToolsManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

mantiene la colección de objetos de [CUserTool Class](../../mfc/reference/cusertool-class.md) en una aplicación.  Una herramienta de usuario es un elemento de menú que ejecuta una aplicación externa.  El objeto de `CUserToolsManager` permite al usuario o el programador para agregar nuevas herramientas de usuario a la aplicación.  Admite la ejecución de los comandos asociados con las herramientas de usuario, y también guarda información sobre las herramientas de usuario en el Registro de Windows.  
  
## Sintaxis  
  
```  
class CUserToolsManager : public CObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUserToolsManager::CUserToolsManager](../Topic/CUserToolsManager::CUserToolsManager.md)|Construye un `CUserToolsManager`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUserToolsManager::CreateNewTool](../Topic/CUserToolsManager::CreateNewTool.md)|Crea una nueva herramienta de usuario.|  
|[CUserToolsManager::FindTool](../Topic/CUserToolsManager::FindTool.md)|Devuelve el puntero al objeto de `CMFCUserTool` que está asociado a un identificador especificada de comando|  
|[CUserToolsManager::GetArgumentsMenuID](../Topic/CUserToolsManager::GetArgumentsMenuID.md)|Devuelve el Id. de recurso que está asociado al menú de **Argumentos** en la pestaña de **Herramientas** del cuadro de diálogo de **Personalizar** .|  
|[CUserToolsManager::GetDefExt](../Topic/CUserToolsManager::GetDefExt.md)|Devuelve la extensión predeterminada que el cuadro de diálogo de **Abrir archivo** \([CFileDialog::CFileDialog](../Topic/CFileDialog::CFileDialog.md)\) utiliza en el campo del comando en la ficha de **Herramientas** del cuadro de diálogo de **Personalizar** .|  
|[CUserToolsManager::GetFilter](../Topic/CUserToolsManager::GetFilter.md)|Devuelve el filtro de archivos que el cuadro de diálogo de **Abrir archivo** \([CFileDialog Class](../../mfc/reference/cfiledialog-class.md)\) utiliza en el campo del comando en la ficha de **Herramientas** del cuadro de diálogo de **Personalizar** .|  
|[CUserToolsManager::GetInitialDirMenuID](../Topic/CUserToolsManager::GetInitialDirMenuID.md)|Devuelve el Id. de recurso que está asociado al menú de **Directorio inicial** en la pestaña de **Herramientas** del cuadro de diálogo de **Personalizar** .|  
|[CUserToolsManager::GetMaxTools](../Topic/CUserToolsManager::GetMaxTools.md)|Devuelve el número máximo de herramientas del usuario que se pueden asignar en la aplicación.|  
|[CUserToolsManager::GetToolsEntryCmd](../Topic/CUserToolsManager::GetToolsEntryCmd.md)|Devuelve el identificador del marcador del elemento de menú para las herramientas de usuario.|  
|[CUserToolsManager::GetUserTools](../Topic/CUserToolsManager::GetUserTools.md)|Devuelve una referencia a la lista de herramientas del usuario.|  
|[CUserToolsManager::InvokeTool](../Topic/CUserToolsManager::InvokeTool.md)|Ejecuta una aplicación asociado al usuario que tiene un identificador especificada de comando|  
|[CUserToolsManager::IsUserToolCmd](../Topic/CUserToolsManager::IsUserToolCmd.md)|Determina si un identificador de comando es asociado con una herramienta de usuario.|  
|[CUserToolsManager::LoadState](../Topic/CUserToolsManager::LoadState.md)|Carga información sobre las herramientas de usuario del Registro de Windows.|  
|[CUserToolsManager::MoveToolDown](../Topic/CUserToolsManager::MoveToolDown.md)|Mueve la herramienta especificada de usuario en la lista de herramientas del usuario.|  
|[CUserToolsManager::MoveToolUp](../Topic/CUserToolsManager::MoveToolUp.md)|Mueve la herramienta especificada del usuario en la lista de herramientas del usuario.|  
|[CUserToolsManager::RemoveTool](../Topic/CUserToolsManager::RemoveTool.md)|Quita la herramienta especificada del usuario de la aplicación.|  
|[CUserToolsManager::SaveState](../Topic/CUserToolsManager::SaveState.md)|Almacena información sobre las herramientas de usuario en el Registro de Windows.|  
|[CUserToolsManager::SetDefExt](../Topic/CUserToolsManager::SetDefExt.md)|Especifica la extensión predeterminada que el cuadro de diálogo de **Abrir archivo** \([CFileDialog Class](../../mfc/reference/cfiledialog-class.md)\) utiliza en el campo del comando en la ficha de **Herramientas** del cuadro de diálogo de **Personalizar** .|  
|[CUserToolsManager::SetFilter](../Topic/CUserToolsManager::SetFilter.md)|Especifica el filtro de archivos que el cuadro de diálogo de **Abrir archivo** \([CFileDialog Class](../../mfc/reference/cfiledialog-class.md)\) utiliza en el campo del comando en la ficha de **Herramientas** del cuadro de diálogo de **Personalizar** .|  
  
## Comentarios  
 Para escribir las herramientas de usuario en la aplicación, debe:  
  
 1.  Reserva un elemento de menú y un identificador asociado de comando para una entrada de menú del usuario.  
  
 2.  Reserva un identificador secuencial command para cada herramienta de usuario que un usuario puede definir en la aplicación.  
  
 3.  Llame al método de [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md) y proporcione los parámetros siguientes: identificador de comando de menú, primer identificador de comando de herramienta de usuario, e identificador del último comando de herramienta de usuario  
  
 Debe haber un objeto de `CUserToolsManager` por la aplicación.  
  
 Para obtener un ejemplo de las herramientas de usuario, vea el proyecto de ejemplo de VisualStudioDemo.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo recuperar una referencia a un objeto de `CUserToolsManager` y cómo crear nuevas herramientas de usuario.  Este fragmento de código es parte de [Ejemplo de demostración de Visual Studio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/CPP/cusertoolsmanager-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)  
  
## Requisitos  
 **encabezado:** afxusertoolsmanager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CUserTool Class](../../mfc/reference/cusertool-class.md)