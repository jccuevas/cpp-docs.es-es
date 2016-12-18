---
title: "Propiedades est&#225;ndar | Microsoft Docs"
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
  - "propiedades estándar"
  - "propiedades estándar, acerca de las propiedades estándar"
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Propiedades est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si va a agregar una propiedad a una interfaz dispinterface de MFC mediante el [Asistente para agregar propiedades](../ide/idl-attributes-add-property-wizard.md), podrá elegir una propiedad estándar de la lista **Nombre de propiedad** en la página [Nombres](../ide/names-add-property-wizard.md) del asistente.  Estas propiedades son las siguientes:  
  
|Nombre de la propiedad.|Descripción|  
|-----------------------------|-----------------|  
|**Apariencia**|Permite obtener o establecer un valor que determina la apariencia del control.  La propiedad **Appearance** del control puede incluir u omitir efectos tridimensionales.  Se trata de una propiedad de ambiente de lectura y escritura.|  
|`BackColor`|Devuelve o establece la propiedad de ambiente `BackColor` del control o en un color de paleta \(RGB\) o en un color de sistema predeterminado.  De forma predeterminada, su valor se corresponde con el color de primer plano del contenedor del control.  Se trata de una propiedad de ambiente de lectura y escritura.|  
|`BorderStyle`|Devuelve o establece el estilo del borde de un control.  Se trata de una propiedad de lectura y escritura.|  
|**Leyenda**|Devuelve o establece la propiedad **Caption** del control.  Esta propiedad corresponde al título de la ventana.  **Caption** no tiene tipo de implementación **Variable miembro**.|  
|**Enabled**|Devuelve o establece la propiedad **Enabled** del control.  Un control habilitado puede responder a eventos generados por el usuario.|  
|**Fuente**|Devuelve o establece la fuente de ambiente del control.  Tomará un valor nulo si el control no tiene texto.|  
|`ForeColor`|Devuelve o establece la propiedad de ambiente `ForeColor` del control.|  
|**hWnd**|Devuelve o establece la propiedad **hWnd** del control.  **hWnd** no tiene un tipo de implementación **Variable miembro**.|  
|**ReadyState**|Devuelve o establece la propiedad **ReadyState** del control.  Un control puede estar: sin inicializar, inicializado, cargando, interactivo o completo.  Vea [READYSTATE](https://msdn.microsoft.com/en-us/library/aa768362.aspx), en el *SDK de Internet*, para obtener más información.|  
|**Text**|Devuelve o establece el texto incluido en un control.  **Text** no tiene tipo de implementación **Variable miembro**.|  
  
## Vea también  
 [Agregar una propiedad](../ide/adding-a-property-visual-cpp.md)   
 [Atributos IDL, Asistente para agregar propiedades](../ide/idl-attributes-add-property-wizard.md)