---
title: "ASP, Asistente para componentes de páginas de Active Server ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.asp.asp
dev_langs: C++
helpviewer_keywords: ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69d3837cc0996c0e0e0784214cfbfa6744afbf94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Asistente para componentes de páginas Active Server ATL
Use esta página del Asistente para componentes de páginas Active Server ATL para especificar la configuración opcional para controlar la información y estado relacionado con el componente ASP.  
  
 **Métodos opcionales**  
 Agrega los métodos ASP opcionales, **OnStartPage** y **OnEndPage**, al objeto. Debe seleccionar esta opción para establecer los objetos intrínsecos de páginas Active Server. De forma predeterminada, está seleccionada.  
  
-   **OnStartPage o OnEndPage** [OnStartPage](https://msdn.microsoft.com/library/ms691624.aspx) se llama por primera vez el script intenta tener acceso al objeto. **OnEndPage** se llama cuando finaliza el objeto de la secuencia de comandos de procesamiento.  
  
 **Objeto intrínseco**  
 Debe seleccionar la **OnStartPage o OnEndPage** opción para establecer los objetos intrínsecos de ASP.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Solicitud**|Proporciona acceso a las páginas Active Server intrínseco **solicitar** objeto. El objeto de solicitud se utiliza para pasar una solicitud HTTP.|  
|**Respuesta**|Proporciona acceso a las páginas Active Server intrínseco **respuesta** objeto. En respuesta a una solicitud, el objeto Response envía información al explorador para mostrar al usuario.|  
|**Sesión**|Proporciona acceso a las páginas Active Server intrínseco **sesión** objeto. El **sesión** objeto mantiene información acerca de la sesión de usuario actual, incluyendo el almacenamiento y recuperación de información de estado.|  
|**Aplicación**|Proporciona acceso a las páginas Active Server intrínseco **aplicación** objeto. El **aplicación** objeto administra el estado que se comparte entre varios objetos ASP.|  
|**Servidor**|Proporciona acceso a las páginas Active Server intrínseco **Server** objeto. El **Server** objeto le permite crear otros objetos ASP.|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para componentes de páginas de Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [Componentes de páginas Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

