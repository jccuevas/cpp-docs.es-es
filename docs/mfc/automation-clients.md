---
title: Los clientes de automatización | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4a4327e1c3e4d65c5bdc3b822cf2cdfc1ec0353
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820599"
---
# <a name="automation-clients"></a>clientes de automatización

Automatización hace posible que la aplicación manipule objetos implementados en otra aplicación o exponga objetos para que se puedan manipular. Un cliente de automatización es una aplicación que puede manipular objetos expuestos por otra aplicación. La aplicación que expone los objetos se denomina el servidor de automatización. El cliente usa objetos de la aplicación de servidor mediante el acceso a propiedades y funciones de esos objetos.

### <a name="types-of-automation-clients"></a>Tipos de clientes de automatización

Hay dos tipos de clientes de automatización:

- Clientes que dinámicamente (en tiempo de ejecución) para obtener información acerca de las propiedades y operaciones del servidor.

- Clientes que poseen información estática (proporcionada en tiempo de compilación) que especifica las propiedades y operaciones del servidor.

Los clientes del primer tipo obtienen información sobre los métodos y propiedades del servidor consultando el sistema OLE `IDispatch` mecanismo. Aunque resulta adecuada que se usará para los clientes dinámicos, `IDispatch` es difícil de usar para clientes estáticos, donde los objetos están impulsando debe conocerse en tiempo de compilación. Para estático enlazado a los clientes, Microsoft Foundation classes proporcionan el [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) clase.

Clientes enlazados estáticos utilizan una clase de proxy que está vinculada estáticamente con la aplicación cliente. Esta clase proporciona una encapsulación de C++ con seguridad de tipos de propiedades y operaciones de la aplicación de servidor.

La clase `COleDispatchDriver` proporciona la compatibilidad para el cliente de automatización de la entidad de seguridad. Mediante el **Agregar nuevo elemento** cuadro de diálogo, crea una clase derivada de `COleDispatchDriver`.

A continuación, especifique el archivo de biblioteca de tipos que describen las propiedades y funciones del objeto de la aplicación de servidor. El cuadro de diálogo Agregar elemento lee este archivo y crea el `COleDispatchDriver`-clase derivada, con las funciones miembro que se puede llamar la aplicación para tener acceso a objetos de la aplicación de servidor en C++, de manera segura para el tipo. Funcionalidad adicional que se hereda de `COleDispatchDriver` simplifica el proceso de llamada al servidor de automatización adecuado.

### <a name="handling-events-in-automation-clients"></a>Control de eventos en los clientes de automatización

Si desea controlar los eventos en el cliente de automatización, deberá agregar una interfaz de receptor. MFC proporciona soporte técnico de Asistente para agregar interfaces de receptor para controles ActiveX, pero no se admite para otros servidores COM. Para obtener información sobre cómo agregar una interfaz de receptor en un cliente MFC para interfaces de origen que se describe en los servidores COM, vea Cómo: crear una interfaz de receptor en el cliente COM de MFC-Based (181845 KB) en [ http://support.microsoft.com/default.aspxscid=kb; 181845](http://support.microsoft.com/default.aspxscid=kb;181845).

## <a name="see-also"></a>Vea también

[Clientes de automatización: Usar bibliotecas de tipos](../mfc/automation-clients-using-type-libraries.md)<br/>
[Automatización](../mfc/automation.md)<br/>
[Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md)

