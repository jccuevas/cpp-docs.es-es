---
title: "CCommandLineInfo Class | Microsoft Docs"
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
  - "CCommandLineInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "application flags [C++]"
  - "argv argument"
  - "CCommandLineInfo class"
  - "línea de comandos, analizar"
  - "analizar, argumentos de la línea de comandos"
  - "código de inicio, parsing command-line arguments"
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommandLineInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Ayuda a analizar la línea de comandos en el inicio de la aplicación.  
  
## Sintaxis  
  
```  
class CCommandLineInfo : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCommandLineInfo::CCommandLineInfo](../Topic/CCommandLineInfo::CCommandLineInfo.md)|Construye un objeto predeterminado de `CCommandLineInfo` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCommandLineInfo::ParseParam](../Topic/CCommandLineInfo::ParseParam.md)|Invalide esta devolución de llamada para analizar parámetros individuales.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCommandLineInfo::m\_bRunAutomated](../Topic/CCommandLineInfo::m_bRunAutomated.md)|Indica que la opción de **\/Automation** de la línea de comandos se encontró.|  
|[CCommandLineInfo::m\_bRunEmbedded](../Topic/CCommandLineInfo::m_bRunEmbedded.md)|Indica que la opción de **\/Embedding** de la línea de comandos se encontró.|  
|[CCommandLineInfo::m\_bShowSplash](../Topic/CCommandLineInfo::m_bShowSplash.md)|Indica si se muestra una pantalla de presentación.|  
|[CCommandLineInfo::m\_nShellCommand](../Topic/CCommandLineInfo::m_nShellCommand.md)|Indica el comando del shell de ser procesado.|  
|[CCommandLineInfo::m\_strDriverName](../Topic/CCommandLineInfo::m_strDriverName.md)|Indica el nombre del controlador si el comando de shell es imprime en; si no está vacío.|  
|[CCommandLineInfo::m\_strFileName](../Topic/CCommandLineInfo::m_strFileName.md)|Indica el nombre de archivo que se abrirá o formulario; vacío si el comando de shell es Nueva o DDE.|  
|[CCommandLineInfo::m\_strPortName](../Topic/CCommandLineInfo::m_strPortName.md)|Indica el nombre de puerto si el comando de shell es imprime en; si no está vacío.|  
|[CCommandLineInfo::m\_strPrinterName](../Topic/CCommandLineInfo::m_strPrinterName.md)|Indica el nombre de la impresora si el comando de shell es imprime en; si no está vacío.|  
|[CCommandLineInfo::m\_strRestartIdentifier](../Topic/CCommandLineInfo::m_strRestartIdentifier.md)|Indica el identificador único del reinicio del administrador de reinicio si el administrador de reinicio reinició la aplicación.|  
  
## Comentarios  
 Una aplicación MFC creará normalmente una instancia local de esta clase en la función de [InitInstance](../Topic/CWinApp::InitInstance.md) del objeto application.  Este objeto se pasa a [CWinApp::ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md), que llama repetidamente [ParseParam](../Topic/CCommandLineInfo::ParseParam.md) para rellenar el objeto de `CCommandLineInfo` .  El objeto de `CCommandLineInfo` se pasa a [CWinApp::ProcessShellCommand](../Topic/CWinApp::ProcessShellCommand.md) para controlar los argumentos de la línea de comandos e indicadores.  
  
 Puede utilizar este objeto para encapsular las opciones de la línea de comandos y parámetros siguientes:  
  
|Argumento de la línea de comandos|Comando ejecutado|  
|---------------------------------------|-----------------------|  
|*aplicación*|Nuevo archivo.|  
|Nombre de archivo de la*aplicación*|Archivo abierto.|  
|Nombre de archivo de**\/p** de la*aplicación*|Archivo de impresión para establecer como valor predeterminado la impresora.|  
|Puerto del controlador de impresora de nombre de archivo de**\/pt***de la aplicación*|Archivo de impresión a la impresora especificada.|  
|*aplicación* **\/dde**|El inicio y espera el comando DDE.|  
|*aplicación* **\/Automation**|Inicio como servidor de automatización OLE.|  
|*aplicación* **\/Embedding**|Edición de inicio hasta un elemento OLE incrustado.|  
|*aplicación* **\/Register**<br /><br /> *aplicación* **\/Regserver**|Informa a la aplicación para realizar cualquier tarea del registro.|  
|*aplicación* **\/Unregister**<br /><br /> *aplicación* **\/Unregserver**|Informa a la aplicación para realizar cualquier tarea de O.N.U\- registro.|  
  
 Derive una nueva clase de `CCommandLineInfo` controle otros marcadores y valores de parámetro.  Reemplazo [ParseParam](../Topic/CCommandLineInfo::ParseParam.md) para controlar los nuevos marcadores.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCommandLineInfo`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWinApp::ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)   
 [CWinApp::ProcessShellCommand](../Topic/CWinApp::ProcessShellCommand.md)