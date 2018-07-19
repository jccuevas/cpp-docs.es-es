---
title: Servidores de automatización | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 337d5a1ec25e8fc80cf867aecef0452b1d03fb2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343949"
---
# <a name="automation-servers"></a>Servidores de automatización
Automatización permite a la aplicación para manipular objetos implementados en otra aplicación o exponga objetos para que se puedan manipular. Un servidor de automatización es una aplicación que expone objetos programables (llamados objetos de automatización) a otras aplicaciones (denominado [los clientes de automatización](../mfc/automation-clients.md)). Servidores de automatización se denominan componentes de automatización.  
  
 Exponer objetos de automatización permite a los clientes automatizar determinados procedimientos accediendo directamente a los objetos y la funcionalidad del servidor hace que estén disponible. La exposición de objetos es beneficiosa si las aplicaciones proporcionan funcionalidad útil para otras aplicaciones. Por ejemplo, un procesador de textos podría exponer su funcionalidad ortográfica para que otros programas puedan usarla. La exposición de objetos permite a los proveedores mejorar la funcionalidad de sus aplicaciones mediante la funcionalidad lista para usar de otras aplicaciones.  
  
 Estos objetos de automatización tienen propiedades y métodos como interfaz externa. Propiedades se denominan atributos del objeto de automatización. Propiedades son similares a los miembros de datos de una clase de C++. Los métodos son funciones que funcionan en objetos de automatización. Los métodos son similares a las funciones de miembro público de una clase de C++.  
  
> [!NOTE]
>  Aunque las propiedades son similares a los miembros de datos de C++, no son accesibles directamente. Para proporcionar un acceso transparente, configure una variable interna del objeto de automatización con un par de funciones miembro get/set para tener acceso a ellos.  
  
 Al exponer la funcionalidad de la aplicación a través de una interfaz común y bien definida, automatización permite crear aplicaciones en un único lenguaje de programación general como Microsoft Visual Basic en lugar de en macro diverso, específica de la aplicación Idiomas.  
  
##  <a name="_core_support_for_automation_servers"></a> Compatibilidad con servidores de automatización  
 Visual C++ y el marco de trabajo MFC proporcionan una amplia compatibilidad para servidores de automatización. Administran gran parte de la sobrecarga implicada en la creación de un servidor de automatización, por lo que se pueda centrar sus esfuerzos en la funcionalidad de la aplicación.  
  
 Mecanismo de entidad de seguridad del marco de trabajo para admitir la automatización es el mapa de envíos, un conjunto de macros que se expande en las declaraciones y las llamadas necesarias para exponer métodos y propiedades para OLE. Un mapa de envíos típico tiene el siguiente aspecto:  
  
 [!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]  
  
 La ventana Propiedades y la vista de clases ayudarle a mantener los mapas de envío. Cuando se agrega un nuevo método o una propiedad a una clase, Visual C++ agrega correspondiente `DISP_FUNCTION` o `DISP_PROPERTY` macro con parámetros que indican el nombre de clase, los nombres internos y externos de los tipos de método o propiedad y los datos.  
  
 El **Agregar clase** cuadro de diálogo también simplifica la declaración de clases de automatización y la administración de sus propiedades y operaciones. Cuando utilice el cuadro de diálogo Agregar clase para agregar una clase al proyecto, especifique su clase base. Si la clase base permite la automatización, el cuadro de diálogo Agregar clase muestra los controles que se utilizan para especificar si la nueva clase debe admitir la automatización, ya sea "OLE que se puede crear" (es decir, si los objetos de la clase se pueden crear en una solicitud de un cliente COM) y el nombre externo para el cliente COM puede utilizar.  
  
 El **Agregar clase** cuadro de diálogo, a continuación, crea una declaración de clase, como las macros apropiadas para la OLE características que haya especificado. También agrega la estructura de código para la implementación de funciones miembro de la clase.  
  
 El Asistente para aplicaciones MFC simplifica los pasos necesarios para la obtención de la aplicación de servidor de automatización del suelo. Si selecciona el **automatización** casilla de verificación de la **características avanzadas** página, el Asistente para aplicaciones MFC agrega a la aplicación `InitInstance` función las llamadas necesarias para registrar la automatización objetos y ejecutar la aplicación como un servidor de automatización.  
  
### <a name="what-do-you-want-to-do"></a>Qué quieres hacer  
  
-   [Obtenga información acerca de los clientes de automatización](../mfc/automation-clients.md)  
  
-   [Más información acerca de la clase CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
  
-   [Más información acerca de la clase COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)  
  
## <a name="see-also"></a>Vea también  
 [Automatización](../mfc/automation.md)   
 [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md)

