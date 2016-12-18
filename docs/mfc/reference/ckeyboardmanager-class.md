---
title: "CKeyboardManager Class | Microsoft Docs"
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
  - "CKeyboardManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CKeyboardManager class"
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CKeyboardManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Administra las tablas de teclas de método abreviado para las ventanas del cuadro de la ventana y secundario de marco principal.  
  
## Sintaxis  
  
```  
class CKeyboardManager : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CKeyboardManager::CKeyboardManager](../Topic/CKeyboardManager::CKeyboardManager.md)|Crea un objeto `CKeyboardManager`.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CKeyboardManager::CleanUp](../Topic/CKeyboardManager::CleanUp.md)|Borra las tablas de teclas de método abreviado.|  
|[CKeyboardManager::FindDefaultAccelerator](../Topic/CKeyboardManager::FindDefaultAccelerator.md)|recupera la tecla de método abreviado predeterminada para el comando y la ventana especificados.|  
|[CKeyboardManager::IsKeyHandled](../Topic/CKeyboardManager::IsKeyHandled.md)|Determina si una clave controla la tabla de aceleradores.|  
|[CKeyboardManager::IsKeyPrintable](../Topic/CKeyboardManager::IsKeyPrintable.md)|indica si un carácter es imprimible.|  
|[CKeyboardManager::IsShowAllAccelerators](../Topic/CKeyboardManager::IsShowAllAccelerators.md)|Indica si los menús muestran todas las teclas de método abreviado para un comando o sólo la tecla de método abreviado predeterminada.|  
|[CKeyboardManager::LoadState](../Topic/CKeyboardManager::LoadState.md)|Carga las tablas de teclas de método abreviado del Registro de Windows.|  
|[CKeyboardManager::ResetAll](../Topic/CKeyboardManager::ResetAll.md)|Cargar las tablas de teclas de método abreviado de recursos de la aplicación.|  
|[CKeyboardManager::SaveState](../Topic/CKeyboardManager::SaveState.md)|Guarda las tablas de teclas de método abreviado al Registro de Windows.|  
|[CKeyboardManager::ShowAllAccelerators](../Topic/CKeyboardManager::ShowAllAccelerators.md)|Especifica si el marco muestra todas las teclas de método abreviado para todos los comandos, o una única tecla de método abreviado para cada comando.  Este método no afecta a los comandos que tienen sólo una tecla de método abreviado asociada.|  
|[CKeyboardManager::TranslateCharToUpper](../Topic/CKeyboardManager::TranslateCharToUpper.md)|Convierte un carácter al registro superior.|  
|[CKeyboardManager::UpdateAccelTable](../Topic/CKeyboardManager::UpdateAccelTable.md)|Actualiza una tabla de teclas de método abreviado con una nueva tabla de teclas de método abreviado.|  
  
## Comentarios  
 Los miembros de esta clase permiten guardar y las tablas de teclas de método abreviado de carga al Registro de Windows, para utilizar una plantilla para actualizar las tablas de la clave de cortar short, y encontrar la tecla de método abreviado predeterminada para un comando en una ventana de marco.  Además, el objeto de `CKeyboardManager` le permite controlar cómo las teclas de método abreviado se presentan al usuario.  
  
 No debe crear un objeto de `CKeyboardManager` manualmente.  Se creará automáticamente el marco de trabajo de la aplicación.  Sin embargo, debe llamar a [CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md) durante el proceso de inicialización de la aplicación.  Para obtener un puntero al administrador de teclado para su aplicación, llame a [CWinAppEx::GetKeyboardManager](../Topic/CWinAppEx::GetKeyboardManager.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo recuperar un puntero a un objeto de `CKeyboardManager` de una clase de `CWinAppEx` , y cómo mostrar todas las teclas de método abreviado asociadas a comandos de menú.  Este fragmento de código es parte de [Ejemplo de las páginas de personalizadas](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/CPP/ckeyboardmanager-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)  
  
## Requisitos  
 **encabezado:** afxkeyboardmanager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md)   
 [Personalización del teclado y del mouse](../../mfc/keyboard-and-mouse-customization.md)