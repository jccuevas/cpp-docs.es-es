---
title: Servidores de automatización
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 4c2ef77e20b7dccfa8cd6830c090111601331642
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619416"
---
# <a name="automation-servers"></a>Servidores de automatización

La automatización permite que la aplicación manipule objetos implementados en otra aplicación o exponga objetos para que se puedan manipular. Un servidor de automatización es una aplicación que expone objetos programables (denominados objetos de automatización) a otras aplicaciones (denominadas [clientes de automatización](automation-clients.md)). Los servidores de automatización a veces se denominan componentes de automatización.

La exposición de objetos de automatización permite a los clientes automatizar determinados procedimientos mediante el acceso directo a los objetos y la funcionalidad que el servidor pone a disposición. Exponer objetos de esta manera es beneficioso cuando las aplicaciones proporcionan funcionalidad útil para otras aplicaciones. Por ejemplo, un procesador de textos podría exponer su funcionalidad de revisión ortográfica para que otros programas puedan usarla. La exposición de objetos permite a los proveedores mejorar la funcionalidad de sus aplicaciones mediante la funcionalidad lista para usar de otras aplicaciones.

Estos objetos de automatización tienen propiedades y métodos como interfaz externa. Las propiedades son atributos con nombre del objeto de automatización. Las propiedades son como los miembros de datos de una clase de C++. Los métodos son funciones que funcionan en objetos de automatización. Los métodos son similares a las funciones miembro públicas de una clase de C++.

> [!NOTE]
> Aunque las propiedades son como los miembros de datos de C++, no son accesibles directamente. Para proporcionar acceso transparente, configure una variable interna en el objeto de automatización con un par de funciones miembro Get/Set para tener acceso a ellas.

Al exponer la funcionalidad de la aplicación mediante una interfaz común y bien definida, la automatización permite compilar aplicaciones en un único lenguaje de programación general, como Microsoft Visual Basic en lugar de en diversos lenguajes de macros específicos de la aplicación.

## <a name="support-for-automation-servers"></a><a name="_core_support_for_automation_servers"></a>Compatibilidad con servidores de Automation

Visual C++ y el marco de trabajo de MFC proporcionan una amplia compatibilidad para los servidores de automatización. Administran gran parte de la sobrecarga que implica la creación de un servidor de automatización, por lo que puede centrar sus esfuerzos en la funcionalidad de la aplicación.

El mecanismo principal del marco de trabajo para la compatibilidad con la automatización es el mapa de envío, un conjunto de macros que se expande en las declaraciones y llamadas necesarias para exponer métodos y propiedades para OLE. Un mapa de envío típico tiene el siguiente aspecto:

[!code-cpp[NVC_MFCAutomation#1](codesnippet/cpp/automation-servers_1.cpp)]

El [Asistente para clases](reference/mfc-class-wizard.md) y vista de clases ayudan en el mantenimiento de las asignaciones de envío. Cuando se agrega un nuevo método o propiedad a una clase, Visual Studio agrega una `DISP_FUNCTION` macro o correspondiente `DISP_PROPERTY` con parámetros que indican el nombre de clase, los nombres externos e internos del método o la propiedad, y los tipos de datos.

El cuadro de diálogo **Agregar clase** también simplifica la declaración de clases de automatización y la administración de sus propiedades y operaciones. Cuando se usa el cuadro de diálogo Agregar clase para agregar una clase al proyecto, se especifica su clase base. Si la clase base permite la automatización, el cuadro de diálogo Agregar clase muestra los controles que se utilizan para especificar si la nueva clase debe admitir la automatización, si se trata de "OLE creatable" (es decir, si los objetos de la clase se pueden crear en una solicitud de un cliente COM) y el nombre externo del cliente COM que se va a usar.

A continuación, el cuadro de diálogo **Agregar clase** crea una declaración de clase, incluidas las macros adecuadas para las características OLE que ha especificado. También agrega el código esqueleto para la implementación de las funciones miembro de la clase.

El Asistente para aplicaciones MFC simplifica los pasos necesarios para desactivar la aplicación de servidor de Automation. Si activa la casilla **Automation** en la página **características avanzadas** , el Asistente para aplicaciones MFC agrega a la función de la aplicación `InitInstance` las llamadas necesarias para registrar los objetos de automatización y ejecutar la aplicación como servidor de automatización.

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Más información sobre los clientes de Automation](automation-clients.md)

- [Más información sobre la clase CCmdTarget](reference/ccmdtarget-class.md)

- [Más información sobre la clase COleDispatchDriver](reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Consulte también

[Automation](automation.md)<br/>
[Asistente para aplicaciones MFC](reference/mfc-application-wizard.md)
