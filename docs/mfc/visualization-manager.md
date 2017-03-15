---
title: "Administrador de visualizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Administrador de visualización"
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Administrador de visualizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El administrador visual es un objeto que controla la apariencia de una aplicación completa.  Actúa como una sola clase donde se puede colocar todo el código de dibujo para la aplicación.  La biblioteca MFC contiene varios administradores visuales.  También puede crear dispone el administrador visual si desea crear una vista personalizada para la aplicación.  Las imágenes muestran la misma aplicación cuando permiten a los administradores visuales:  
  
 ![MyApp tal y como la presenta CMFCVisualManagerWindows](../mfc/media/vmwindows.png "VMWindows")  
MyApp que utiliza el administrador de la representación visual de CMFCVisualManagerWindows  
  
 ![MyApp tal y como la presenta CMFCVisualManagerVS2005](../mfc/media/vmvs2005.png "VMVS2005")  
MyApp que utiliza el administrador de representación visual CMFCVisualManagerVS2005  
  
 ![MyApp tal y como la presenta CMFCVisualManagerOfficeXP](../mfc/media/vmofficexp.png "VMOfficeXP")  
MyApp que utiliza el administrador de la representación visual de CMFCVisualManagerOfficeXP  
  
 ![MyApp tal y como la presenta CMFCVisualManagerOffice2003](../mfc/media/vmoffice2003.png "VMOffice2003")  
MyApp que utiliza el administrador de representación visual CMFCVisualManagerOffice2003  
  
 ![MyApp tal y como la presenta CMFCVisualManagerOffice2007](../mfc/media/msoffice2007.png "MSOffice2007")  
MyApp que utiliza el administrador de representación visual CMFCVisualManagerOffice2007  
  
 De forma predeterminada, el administrador visual mantiene el código de dibujo para varios elementos de GUI.  Para proporcionar elementos personalizados de interfaz de usuario, debe invalidar los métodos relacionados del gráfico de administrador visual.  Para la lista de estos métodos, vea [CMFCVisualManager Class](../mfc/reference/cmfcvisualmanager-class.md).  Los métodos que puede reemplazar para proporcionar un aspecto personalizado son todos los métodos que comienzan con `OnDraw`.  
  
 La aplicación puede tener un solo objeto de `CMFCVisualManager` .  Para obtener un puntero al administrador visual para la aplicación, llame a la función estática [CMFCVisualManager::GetInstance](../Topic/CMFCVisualManager::GetInstance.md).  Dado que todos los administradores visuales heredan de `CMFCVisualManager`, el método de `CMFCVisualManager::GetInstance` obtendrán un puntero al administrador visual adecuado, incluso si se crea un administrador visual personalizado.  
  
 Si desea crear un administrador visual personalizado, debe derivarlo de un administrador visual que ya existe.  La clase predeterminada a derivar de es `CMFCVisualManager`.  Sin embargo, con otro administrador visual si se parece mejor a lo que desea para la aplicación.  Por ejemplo, si desea utilizar el administrador visual de `CMFCVisualManagerOffice2007` , pero deseado para cambiar solo cómo separadores apariencia, puede derivar la clase personalizada de `CMFCVisualManagerOffice2007`.  En este escenario, debe sobrescribir únicamente los métodos para dibujar los separadores.  
  
 Hay dos posibles maneras de utilizar un administrador visual concreto para la aplicación.  Una consiste en llamar al método de [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md) y pasar el administrador visual adecuado como parámetro.  El ejemplo de código siguiente se muestra cómo utilizar el administrador visual de `CMFCVisualManagerVS2005` con este método:  
  
```  
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));  
```  
  
 La otra forma de utilizar un administrador visual en la aplicación es hacerlo manualmente.  La aplicación a continuación utilizará en este nuevo administrador visual para toda la representación.  Sin embargo, dado que solo puede haber un objeto de `CMFCVisualManager` por la aplicación, tendrá que eliminar el administrador visual actual antes de crear un nuevo.  En el ejemplo siguiente, `CMyVisualManager` es un administrador visual personalizado que se deriva de `CMFCVisualManager`.  El método siguiente cambiará utilizan a qué administrador visual para mostrar la aplicación, en función de un índice:  
  
```  
void CMyApp::SetSkin (int index)  
{  
   if (CMFCVisualManager::GetInstance() != NULL)  
   {  
      delete CMFCVisualManager::GetInstance();  
   }  
  
   switch (index)  
   {  
   case DEFAULT_STYLE:  
      // The following statement creates a new CMFCVisualManager  
      CMFCVisualManager::GetInstance();  
      break;  
  
   case CUSTOM_STYLE:  
      new CMyVisualManager;  
      break;  
  
   default:  
      CMFCVisualManager::GetInstance();  
      break;  
   }  
  
   CMFCVisualManager::GetInstance()->RedrawAll();  
}  
```  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [CMFCVisualManager Class](../mfc/reference/cmfcvisualmanager-class.md)