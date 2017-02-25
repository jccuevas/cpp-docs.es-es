---
title: "CUserTool Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CUserTool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUserTool class"
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CUserTool Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una herramienta de usuario es un elemento de menú que ejecuta una aplicación externa.  La ficha de **Herramientas** del cuadro de diálogo de **Personalizar** \([CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)\) permita agregar las herramientas de usuario, y especificar el nombre, el comando, los argumentos, y el directorio inicial para cada herramienta de usuario.  
  
## Sintaxis  
  
```  
class CUserTool : public CObject  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUserTool::CopyIconToClipboard](../Topic/CUserTool::CopyIconToClipboard.md)||  
|[CUserTool::DrawToolIcon](../Topic/CUserTool::DrawToolIcon.md)|Dibuja el icono del usuario en un rectángulo especificado.|  
|[CUserTool::GetCommand](../Topic/CUserTool::GetCommand.md)|Devuelve una cadena que contiene el texto del comando asociado al usuario.|  
|[CUserTool::GetCommandId](../Topic/CUserTool::GetCommandId.md)|Devuelve el identificador del elemento de menú del usuario.|  
|[CUserTool::Invoke](../Topic/CUserTool::Invoke.md)|Ejecuta el comando asociado al usuario.|  
|[CUserTool::Serialize](../Topic/CUserTool::Serialize.md)|Lee o escribe este objeto o un archivo.  \(Reemplaza [CObject::Serialize](../Topic/CObject::Serialize.md).\)|  
|[CUserTool::SetCommand](../Topic/CUserTool::SetCommand.md)|Establece el comando asociado al usuario.|  
|[CUserTool::SetToolIcon](../Topic/CUserTool::SetToolIcon.md)|Carga el icono para el usuario de la aplicación asociada con la herramienta.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUserTool::LoadDefaultIcon](../Topic/CUserTool::LoadDefaultIcon.md)|Carga el icono predeterminado para una herramienta de usuario.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CUserTool::m\_strArguments](../Topic/CUserTool::m_strArguments.md)|Los argumentos de la línea de comandos para la herramienta de usuario.|  
|[CUserTool::m\_strInitialDirectory](../Topic/CUserTool::m_strInitialDirectory.md)|El directorio inicial para el usuario.|  
|[CUserTool::m\_strLabel](../Topic/CUserTool::m_strLabel.md)|El nombre de la herramienta que se muestra en el elemento de menú para la herramienta.|  
  
## Comentarios  
 Para obtener más información sobre cómo habilitar las herramientas de usuario en la aplicación, vea [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo crear una herramienta de un objeto de `CUserToolsManager` , establece la variable miembro de `m_strLabel` , y establece la aplicación que el usuario ejecuta.  Este fragmento de código es parte de [Ejemplo de demostración de Visual Studio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/CPP/cusertool-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## Requisitos  
 **encabezado:** afxusertool.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md)