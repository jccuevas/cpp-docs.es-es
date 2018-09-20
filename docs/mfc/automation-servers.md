---
title: Servidores de automatización | Microsoft Docs
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
ms.openlocfilehash: 2cc163559b4946626e754b70a1b54d4fe20306c7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377623"
---
# <a name="automation-servers"></a>Servidores de automatización

Automatización hace posible que la aplicación manipule objetos implementados en otra aplicación o exponga objetos para que se puedan manipular. Un servidor de automatización es una aplicación que expone objetos programables (denominados objetos de automatización) a otras aplicaciones (llamado [los clientes de automatización](../mfc/automation-clients.md)). Servidores de automatización se denominan a veces, los componentes de automatización.

Exponer objetos de automatización permite a los clientes automatizar determinados procedimientos accediendo directamente a los objetos y hace que esté disponible la funcionalidad del servidor. La exposición de objetos es beneficiosa si las aplicaciones proporcionan funcionalidad que es útil para otras aplicaciones. Por ejemplo, un procesador de textos podría exponer su funcionalidad corrector ortográfico para que otros programas pueden usarlo. La exposición de objetos permite a los proveedores mejorar la funcionalidad de sus aplicaciones mediante la funcionalidad de otras aplicaciones listas para usar.

Estos objetos de automatización tienen propiedades y métodos que su interfaz externa. Las propiedades se denominan los atributos del objeto de automatización. Las propiedades son como los miembros de datos de una clase de C++. Los métodos son funciones que funcionan en objetos de automatización. Los métodos son similares a las funciones miembro públicas de una clase de C++.

> [!NOTE]
>  Aunque las propiedades son iguales que los miembros de datos de C++, no son accesibles directamente. Para proporcionar acceso transparente, configurar una variable interna en el objeto de automatización con un par de funciones miembro get/set para tener acceso a ellos.

Al exponer la funcionalidad de la aplicación a través de una interfaz común bien definida, Automation permite crear aplicaciones en un único lenguaje de programación general, como Microsoft Visual Basic en lugar de en macro diverso, específica de la aplicación Idiomas.

##  <a name="_core_support_for_automation_servers"></a> Compatibilidad con servidores de automatización

Visual C++ y el marco de trabajo MFC proporcionan una amplia compatibilidad para servidores de automatización. Permiten controlar gran parte de la sobrecarga implicada en la creación de un servidor de automatización, por lo que puede centrar sus esfuerzos en la funcionalidad de la aplicación.

Mecanismo de entidad de seguridad de .NET framework para admitir la automatización es el mapa de envíos, un conjunto de macros que se expande en las declaraciones y las llamadas necesarias para exponer métodos y propiedades de OLE. Un mapa de envíos típica tiene este aspecto:

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

La ventana Propiedades y vista de clases ayudar a mantener los mapas de envío. Cuando se agrega un nuevo método o propiedad a una clase, Visual C++ agrega correspondiente `DISP_FUNCTION` o `DISP_PROPERTY` macro con parámetros que indican el nombre de clase, los nombres internos y externos de los tipos de método o propiedad y los datos.

El **Agregar clase** cuadro de diálogo también simplifica la declaración de clases de automatización y la administración de sus propiedades y operaciones. Cuando utilice el cuadro de diálogo Agregar clase para agregar una clase al proyecto, especifique su clase base. Si la clase base permite la automatización, el cuadro de diálogo Agregar clase muestra los controles que se utilizan para especificar si la nueva clase debe admitir la automatización, ya sea "OLE que se puede crear" (es decir, si los objetos de la clase pueden crearse en una solicitud de un cliente COM) y el nombre para que utilice el cliente COM externo.

El **Agregar clase** cuadro de diálogo, a continuación, crea una declaración de clase, incluidas las macros adecuadas para características de OLE que ha especificado. También agrega el código del esqueleto para la implementación de funciones miembro de la clase.

El Asistente para aplicaciones MFC simplifica los pasos necesarios para conseguir que la aplicación de servidor de automatización en marcha. Si selecciona el **automatización** casilla de verificación de la **características avanzadas** página, el Asistente para aplicaciones MFC se agrega a la aplicación `InitInstance` funcionar las llamadas necesarias para registrar la automatización los objetos y ejecutar la aplicación como un servidor de automatización.

### <a name="what-do-you-want-to-do"></a>Qué quieres hacer

- [Obtenga información acerca de los clientes de automatización](../mfc/automation-clients.md)

- [Más información acerca de la clase CCmdTarget](../mfc/reference/ccmdtarget-class.md)

- [Más información acerca de la clase COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Vea también

[Automatización](../mfc/automation.md)<br/>
[Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md)

