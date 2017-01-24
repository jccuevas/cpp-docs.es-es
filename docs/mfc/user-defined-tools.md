---
title: "Herramientas definidas por el usuario | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "herramientas definidas por el usuario (extensiones MFC)"
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Herramientas definidas por el usuario
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC admite las herramientas definido por el usuario.  Una herramienta definido por el usuario es un comando especial que ejecuta un programa externo, definido por el usuario.  Puede utilizar el proceso de personalización para administrar las herramientas definido por el usuario.  Sin embargo, no puede utilizar este proceso si el objeto application no se deriva de [CWinAppEx Class](../mfc/reference/cwinappex-class.md).  Para obtener más información sobre la personalización, vea [Personalización de MFC](../mfc/customization-for-mfc.md).  
  
 Si se compatibilidad definido por el usuario habilitado de herramientas, el cuadro de diálogo personalización automáticamente incluye la ficha de **Herramientas** .  La ilustración siguiente se muestra la página de **Herramientas** .  
  
 ![Pestaña Herramientas del cuadro de diálogo Personalizar](../mfc/media/custdialogboxtoolstab.png "CustDialogBoxToolsTab")  
Pestaña herramientas de cuadro de diálogo personalización  
  
## Habilitar compatibilidad definido por el usuario de las herramientas  
 Para habilitar las herramientas definido por el usuario en una aplicación, llame a [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md).  Sin embargo, primero debe definir varias constantes en los archivos de recursos de la aplicación para utilizar como parámetros para esta llamada.  
  
 En el editor de recursos cree un comando ficticio que utiliza un identificador de comando apropiada  En el ejemplo siguiente, se usa **ID\_TOOLS\_ENTRY** como el identificador de comando  Este identificador de comando marca una ubicación en uno o más menús donde el marco insertará herramientas definido por el usuario.  
  
 Debe incluir algunos id. a un lado consecutivos en la tabla de cadenas para representar las herramientas definido por el usuario.  El número de cadenas que a un lado incluya es igual al número máximo de herramientas del usuario que los usuarios pueden definir.  En el ejemplo siguiente, éstas se denominan **ID\_USER\_TOOL1** con **ID\_USER\_TOOL10**.  
  
 Puede proporcionar sugerencias a los usuarios como ayuda para seleccionar directorios y los argumentos para programas externos que se llamará como herramientas.  Para ello, cree dos menús emergentes en el editor de recursos.  En el ejemplo siguiente se llama **IDR\_MENU\_ARGS** y **IDR\_MENU\_DIRS**.  Para cada comando en los menús, defina una cadena en la tabla de cadenas de la aplicación.  El Id. de recurso de cadena debe ser igual al identificador de comando  
  
 También puede crear una clase derivada de [CUserTool Class](../mfc/reference/cusertool-class.md) para reemplazar la implementación predeterminada.  Para ello, pase la información en tiempo de ejecución para la clase derivada como el cuarto parámetro en CWinAppEx::EnableUserTools, en lugar de RUNTIME\_CLASS \([CUserTool Class](../mfc/reference/cusertool-class.md)\).  
  
 Después de definir las constantes adecuadas, llamada [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md) para habilitar las herramientas definido por el usuario.  
  
 La llamada siguiente muestra cómo usar estas constantes:  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/CPP/user-defined-tools_1.cpp)]  
  
 En este ejemplo, la ficha de herramientas se incluirá en el cuadro de diálogo de **Personalización** .  El marco reemplazará cualquier comando que coincide con el identificador **ID\_TOOLS\_ENTRY** de comando en cualquier menú con el conjunto de herramientas definidas de usuario siempre que abra un usuario ese menú.  Los id. **ID\_USER\_TOOL1** de comando con **ID\_USER\_TOOL10** se reservan para el uso de las herramientas definido por el usuario.  La clase [CUserTool Class](../mfc/reference/cusertool-class.md) controla llamadas a las herramientas de usuario.  La ficha del cuadro de diálogo de **Personalización** proporciona botones a la derecha de los campos de argumento y la entrada en la guía para tener acceso a los menús **IDR\_MENU\_ARGS** y **IDR\_MENU\_DIRS**.que Cuando un usuario selecciona un comando desde uno de los menús, el marco de trabajo anexa al cuadro de texto adecuado la cadena que tiene el Id. de recurso igual al identificador de comando  
  
### Incluidas las herramientas predefinidas  
 Si desea predefinir algunas herramientas en el inicio de la aplicación, debe reemplazar el método de [CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md) de la ventana principal de la aplicación.  En ese método, debe realizar los pasos siguientes.  
  
##### Para agregar nuevas herramientas en LoadFrame  
  
1.  Obtenga un puntero al objeto de [CUserToolsManager Class](../mfc/reference/cusertoolsmanager-class.md) llamando a [CWinAppEx::GetUserToolsManager](../Topic/CWinAppEx::GetUserToolsManager.md).  
  
2.  Para cada herramienta que desea crear, llamada [CUserToolsManager::CreateNewTool](../Topic/CUserToolsManager::CreateNewTool.md).  Este método devuelve un puntero a un objeto de [CUserTool Class](../mfc/reference/cusertool-class.md) y agrega la herramienta creada recientemente de usuario a la colección interna de herramientas.  Si se proporcionó información en tiempo de ejecución para una clase derivada de [CUserTool Class](../mfc/reference/cusertool-class.md) como el cuarto parámetro de [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md), [CUserToolsManager::CreateNewTool](../Topic/CUserToolsManager::CreateNewTool.md) creará instancias y devolverá una instancia de esa clase.  
  
3.  Para cada herramienta, establezca su etiqueta de texto estableciendo `CUserTool::m_strLabel` y establezca su comando llamando a `CUserTool::SetCommand`.  La implementación predeterminada de [CUserTool Class](../mfc/reference/cusertool-class.md) recupera automáticamente iconos disponibles del programa que se especifica en la llamada a `SetCommand`.  
  
## Vea también  
 [Personalización de MFC](../mfc/customization-for-mfc.md)   
 [CUserTool Class](../mfc/reference/cusertool-class.md)   
 [CUserToolsManager Class](../mfc/reference/cusertoolsmanager-class.md)   
 [CWinAppEx Class](../mfc/reference/cwinappex-class.md)