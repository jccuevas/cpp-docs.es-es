---
title: "Specifying Property Pages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ISpecifyPropertyPages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISpecifyPropertyPages method"
  - "páginas de propiedades, especificar"
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Specifying Property Pages
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando crea un control ActiveX, con frecuencia deseará para asociarlo a las páginas de propiedades que se pueden utilizar para establecer las propiedades del control.  Los contenedores de controles utilizan la interfaz de **ISpecifyPropertyPages** para comprobar que las páginas de propiedades se pueden utilizar para establecer las propiedades del control.  Deberá implementar esta interfaz en el control.  
  
 Para implementar **ISpecifyPropertyPages** mediante ATL, siga estos pasos:  
  
1.  derive la clase de [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md).  
  
2.  Agregue una entrada para **ISpecifyPropertyPages** al mapa COM de la clase.  
  
3.  Agregue una entrada de [PROP\_PAGE](../Topic/PROP_PAGE.md) al mapa de propiedades para cada página asociado al control.  
  
> [!NOTE]
>  Al generar un control estándar mediante [Asistente para controles ATL](../atl/reference/atl-control-wizard.md), tendrá que agregar las entradas de `PROP_PAGE` a la asignación de la propiedad.  El asistente genera el código necesario para los demás pasos.  
  
 Los buenos contenedores mostrará las páginas de propiedades especificadas en el mismo orden que las entradas de `PROP_PAGE` en el mapa de propiedades.  Normalmente, debe colocar entradas estándar de la página de propiedades después de que las entradas para las páginas personalizadas en el mapa de propiedades, de modo que los usuarios vean las páginas específicas del control primero.  
  
## Ejemplo  
 La clase siguiente para un control de calendario utiliza la interfaz de **ISpecifyPropertyPages** para indicar a contenedores que sus propiedades se pueden establecer mediante una página personalizada de la fecha y la página en color común.  
  
 [!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/CPP/specifying-property-pages_1.h)]  
  
## Vea también  
 [Páginas de propiedades](../atl/atl-com-property-pages.md)   
 [Ejemplo ATLPages](../top/visual-cpp-samples.md)