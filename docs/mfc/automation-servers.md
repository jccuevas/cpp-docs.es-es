---
title: Servidores de automatización
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 391cb2f6ff5673296f40e21113e3a6510f71d475
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370836"
---
# <a name="automation-servers"></a>Servidores de automatización

La automatización permite que la aplicación manipule objetos implementados en otra aplicación o exponga objetos para que se puedan manipular. Un servidor de automation es una aplicación que expone objetos programables (denominados objetos de automatización) a otras aplicaciones [(denominadas clientes](../mfc/automation-clients.md)de automatización). Los servidores de automatización a veces se denominan componentes de automatización.

La exposición de objetos de automatización permite a los clientes automatizar determinados procedimientos accediendo directamente a los objetos y la funcionalidad que el servidor pone a disposición. Exponer objetos de esta manera es beneficioso cuando las aplicaciones proporcionan funcionalidad que es útil para otras aplicaciones. Por ejemplo, un procesador de textos podría exponer su funcionalidad de corrección ortográfica para que otros programas puedan usarla. La exposición de objetos permite a los proveedores mejorar la funcionalidad de sus aplicaciones mediante la funcionalidad ya preparada de otras aplicaciones.

Estos objetos Automation tienen propiedades y métodos como interfaz externa. Las propiedades se denominan atributos del objeto Automation. Las propiedades son como los miembros de datos de una clase C++. Los métodos son funciones que funcionan en objetos de automatización. Los métodos son como las funciones miembro públicas de una clase C++.

> [!NOTE]
> Aunque las propiedades son como los miembros de datos C++, no son directamente accesibles. Para proporcionar acceso transparente, configure una variable interna en el objeto Automation con un par de funciones miembro get/set para tener acceso a ellas.

Al exponer la funcionalidad de la aplicación a través de una interfaz común y bien definida, Automation permite crear aplicaciones en un único lenguaje de programación general como Microsoft Visual Basic en lugar de en diversos lenguajes de macros específicos específicos de la aplicación.

## <a name="support-for-automation-servers"></a><a name="_core_support_for_automation_servers"></a>Soporte para servidores de automatización

Visual C++ y el marco MFC proporcionan una amplia compatibilidad con los servidores de automatización. Se encargan de gran parte de la sobrecarga que implica crear un servidor de automatización, por lo que puede centrar sus esfuerzos en la funcionalidad de la aplicación.

El mecanismo principal del marco de trabajo para admitir la automatización es el mapa de distribución, un conjunto de macros que se expande en las declaraciones y llamadas necesarias para exponer métodos y propiedades para OLE. Un mapa de envío típico tiene este aspecto:

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

El [Asistente para clases](reference/mfc-class-wizard.md) y la vista de clases ayudan a mantener mapas de distribución. Al agregar un nuevo método o propiedad a una `DISP_FUNCTION` clase, Visual Studio agrega un correspondiente o `DISP_PROPERTY` macro con parámetros que indican el nombre de clase, los nombres externos e internos del método o propiedad y los tipos de datos.

El cuadro de diálogo **Agregar clase** también simplifica la declaración de clases de Automation y la administración de sus propiedades y operaciones. Cuando se utiliza el cuadro de diálogo Agregar clase para agregar una clase al proyecto, se especifica su clase base. Si la clase base permite Automatización, el cuadro de diálogo Agregar clase muestra los controles que se usan para especificar si la nueva clase debe admitir Automatización, si es "OLE creable" (es decir, si se pueden crear objetos de la clase en una solicitud de un cliente COM) y el nombre externo que debe usar el cliente COM.

El cuadro de diálogo **Agregar clase** crea una declaración de clase, incluidas las macros adecuadas para las características OLE que ha especificado. También agrega el código de esqueleto para la implementación de las funciones miembro de la clase.

El Asistente para aplicaciones MFC simplifica los pasos necesarios para sacar la aplicación de servidor de automatización. Si activa la casilla **de verificación Automatización** en la página Características `InitInstance` **avanzadas,** el Asistente para aplicaciones MFC agrega a la función de la aplicación las llamadas necesarias para registrar los objetos de automatización y ejecutar la aplicación como un servidor de automatización.

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Más información sobre los clientes de Automation](../mfc/automation-clients.md)

- [Más información sobre la clase CCmdTarget](../mfc/reference/ccmdtarget-class.md)

- [Más información sobre la clase COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Consulte también

[Automation](../mfc/automation.md)<br/>
[Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md)
