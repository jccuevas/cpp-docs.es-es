---
title: "Controlar el bot&#243;n Aplicar | Microsoft Docs"
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
  - "botón Aplicar de la hoja de propiedades"
  - "hoja de propiedades, botón Aplicar"
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Controlar el bot&#243;n Aplicar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las hojas de propiedades tienen una capacidad que no lo necesitan los cuadros de diálogo estándar: Permiten al usuario aplicar cambios que han realizado antes de cerrar la hoja de propiedades.  Esto se realiza mediante el botón aplicar.  Este artículo se exponen métodos que puede utilizar para implementar esta característica correctamente.  
  
 Los cuadros de diálogo modales suelen aplicar los valores a un objeto externo cuando el usuario hace clic en ACEPTAR para cerrar el cuadro de diálogo.  Lo mismo se aplica a una hoja de propiedades: Cuando el usuario hace clic en ACEPTAR, los nuevos valores en la hoja de propiedades surten efecto.  
  
 Sin embargo, puede ser conveniente permitir al usuario guardar valores sin tener que cerrar el cuadro de diálogo de la hoja de propiedades.  Ésta es la función del botón de aplicar.  El botón de aplicar aplica la configuración actual de todas las páginas de propiedades al objeto externo, en comparación con aplicar únicamente las configuraciones actuales actual de la página activa.  
  
 De forma predeterminada, el botón apply se deshabilita siempre.  Debe escribir código para habilitar el botón apply en los tiempos adecuados, deberá escribir código para implementar el efecto Apply, como se explica más adelante.  
  
 Si no desea proporcionar la funcionalidad de aplicar al usuario, no es necesario quitar el botón de aplicar.  Puede dejar que deshabilitado, como es habitual entre las aplicaciones que utilizan la compatibilidad estándar de la hoja de propiedades disponibles en las versiones de Windows futuras.  
  
 Para designar una página como que modifique y habilitar el botón de aplicar, llamada **CPropertyPage::SetModified\( TRUE \)**.  Si las páginas cualquiera de los señalan la modificación, el botón de aplicar permanecerá habilitado, independientemente de si actualmente se ha modificado la página activa.  
  
 Debe llamar a [CPropertyPage::SetModified](../Topic/CPropertyPage::SetModified.md) siempre que el usuario cambia los valores de la página.  Una forma de detectar cuando un usuario cambia un valor en la página es implementar controladores de notificación para cada uno de los controles en la página de propiedades, como **EN\_CHANGE** o **BN\_CLICKED**.  
  
 Para implementar el efecto del botón de aplicar, la hoja de propiedades debe indicar el propietario, o algún otro objeto externo en la aplicación, aplicar la configuración actual de las páginas de propiedades.  Al mismo tiempo, la hoja de propiedades debe deshabilitar el botón apply llamando a **CPropertyPage::SetModified\( FALSE \)** para todas las páginas que se aplican las modificaciones el objeto externo.  
  
 Para obtener un ejemplo de este proceso, vea el ejemplo [PROPDLG](../top/visual-cpp-samples.md)MFC General.  
  
## Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)