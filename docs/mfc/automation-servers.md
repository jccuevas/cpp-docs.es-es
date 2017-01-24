---
title: "Servidores de automatizaci&#243;n | Microsoft Docs"
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
  - "servidores de automatización"
  - "componentes COM, servidores de automatización"
  - "mapas de envío, servidores de automatización"
  - "servidores, automatización"
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Servidores de automatizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La automatización permite a la aplicación manipular los objetos implementados en otra aplicación, o exponer objetos para que puedan ser manipulados.  Un servidor de automatización es una aplicación que expone objetos programables \(denominados objetos de Automation\) a otras aplicaciones \(denominadas [Clientes de automatización](../mfc/automation-clients.md)\).  Se llama a los servidores de automatización a veces los componentes de Automation.  
  
 Exponer objetos de automatización permite a los clientes para automatizar algunos procedimientos tener acceso directamente a los objetos y funcionalidad que crea el servidor disponible.  Expone objetos de esta manera es beneficiosa cuando las aplicaciones proporcionan funcionalidad que es útil para otras aplicaciones.  Por ejemplo, un procesador de textos podría exponer la funcionalidad de corrección ortográfica de modo que otros programas puedan utilizarla.  La exposición de objetos permite junto a los proveedores para mejorar las funciones de las aplicaciones mediante las funciones confeccionadas de otras aplicaciones.  
  
 Estos objetos de automatización tienen propiedades y métodos como interfaz externa.  Las propiedades se denominan los atributos del objeto de automatización.  Las propiedades son como los miembros de datos de clase de c\+\+.  Los métodos son funciones que funcionan en objetos de automatización.  Los métodos son similares a las funciones públicas del miembro de la clase en cuestión.  
  
> [!NOTE]
>  Aunque las propiedades son como los miembros de datos de C\+\+, no son directamente accesibles.  Para proporcionar acceso transparente, configurar una variable interna en el objeto de automatización con un par de get\/set funciones miembro para tener acceso a ellos.  
  
 Expone la funcionalidad de la aplicación a través de una interfaz común, bien definido, automatización permite compilar aplicaciones de un único lenguaje de programación general como Microsoft Visual Basic en lugar de en macrolenguajes diferentes, específicos de la aplicación.  
  
##  <a name="_core_support_for_automation_servers"></a> Compatibilidad con los servidores de automatización  
 Visual C\+\+ y de MFC proporcionan amplia compatibilidad para servidores de automatización.  Controlan en gran medida la sobrecarga implicada en crear un servidor de automatización, por lo que puede centrar los esfuerzos en la funcionalidad de la aplicación.  
  
 El mecanismo principal del marco para admitir automatización es el mapa send, conjunto de macros que expanda en las declaraciones y llame a necesario para exponer métodos y propiedades para OLE.  Un mapa típico de distribución tiene el siguiente aspecto:  
  
 [!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/CPP/automation-servers_1.cpp)]  
  
 Ayuda de la ventana de Propiedades y la clase en mapas de envío que mantienen.  Cuando se agrega un nuevo método o propiedad a una clase, Visual C\+\+ agrega `DISP_FUNCTION` o una macro correspondiente de `DISP_PROPERTY` con parámetros que indican el nombre de clase, externo y los nombres internos de método o propiedad, y los tipos de datos.  
  
 El cuadro de diálogo de **Agregar clase** también simplifica la declaración de clases de automatización y administración de sus propiedades y operaciones.  Cuando se utiliza el cuadro de diálogo agregar clase para agregar una clase al proyecto, puede especificar su clase base.  Si la clase base permite la automatización, los controles de muestra el cuadro de diálogo agregar clase que se utiliza para especificar si la nueva clase debe admitir la automatización, si es “OLE pueden” \(es decir, si los objetos de la clase se pueden crear en una solicitud de un cliente COM\), y el nombre externo para que el cliente COM que utilice.  
  
 El cuadro de diálogo de **Agregar clase** crea una declaración de clase, incluidas las macros adecuadas para las características de OLE que ha especificado.  También agrega el código estructural para la implementación de las funciones miembro de clases.  
  
 El asistente para aplicaciones MFC simplifica los pasos necesarios para obtener la aplicación de servidor de automatización en segundo plano.  Si activa la casilla de **Automatización** de la página de **Características avanzadas** , Asistente para aplicaciones MFC agrega a la función de `InitInstance` de la aplicación las llamadas necesarias registrar los objetos de automatización y ejecutar la aplicación como servidor de automatización.  
  
### ¿Qué desea hacer?  
  
-   [Obtenga información sobre los clientes de automatización](../mfc/automation-clients.md)  
  
-   [Obtenga más información sobre la clase CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
  
-   [Obtenga más información sobre la clase COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)  
  
## Vea también  
 [automatización](../mfc/automation.md)   
 [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md)