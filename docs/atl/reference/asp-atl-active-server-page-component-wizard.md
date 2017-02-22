---
title: "ASP, Asistente para componentes de p&#225;ginas Active Server ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.asp.asp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para componentes de páginas Active Server ATL, ASP"
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# ASP, Asistente para componentes de p&#225;ginas Active Server ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Use esta página del Asistente para componentes de páginas Active Server ATL si desea especificar una configuración opcional en el control de información y estado relativos a un componente ASP.  
  
 **Métodos opcionales**  
 Agrega los métodos ASP opcionales, **OnStartPage** y **OnEndPage**, al proyecto.  Debe activarse esta opción para establecer objetos intrínsecos de páginas Active Server.  De forma predeterminada está activada.  
  
-   **OnStartPage\/OnEndPage** Se llama a [OnStartPage](https://msdn.microsoft.com/en-us/library/ms691624.aspx) la primera vez que el script intenta obtener acceso al objeto.  Se llama a **OnEndPage** cuando el objeto termina de procesar el script.  
  
 **Objeto intrínseco**  
 Se debe activar la opción **OnStartPage\/OnEndPage** para establecer objetos intrínsecos ASP.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Solicitud**|Proporciona acceso al objeto intrínseco **Request** de las páginas Active Server.  El objeto Request se utiliza para pasar una solicitud HTTP.|  
|**Response**|Proporciona acceso al objeto intrínseco **Response** de las páginas Active Server.  En respuesta a una solicitud, el objeto Response envía información al explorador web que se presenta al usuario.|  
|**Session**|Proporciona acceso al objeto intrínseco **Session** de las páginas Active Server.  El objeto **Session** mantiene información sobre la sesión actual del usuario, almacenando y recuperación información de estado.|  
|**Application**|Proporciona acceso al objeto intrínseco **Application** de las páginas Active Server.  El objeto **Application** administra el estado compartido por varios objetos ASP.|  
|**Servidor**|Proporciona acceso al objeto intrínseco **Server** de las páginas Active Server.  El objeto **Server** permite crear otros objetos ASP.|  
  
## Vea también  
 [Asistente para componentes de páginas Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [ATL Active Server Page Component](../../atl/reference/adding-an-atl-active-server-page-component.md)