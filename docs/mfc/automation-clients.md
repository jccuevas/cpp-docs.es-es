---
title: clientes de automatización
ms.date: 11/04/2016
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
ms.openlocfilehash: 9c34f6fccd06635dfb686e6eb1f2cf895bb86989
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626083"
---
# <a name="automation-clients"></a>clientes de automatización

La automatización permite que la aplicación manipule objetos implementados en otra aplicación o exponga objetos para que se puedan manipular. Un cliente de automatización es una aplicación que puede manipular objetos expuestos que pertenecen a otra aplicación. La aplicación que expone los objetos se denomina servidor de automatización. El cliente manipula los objetos de la aplicación de servidor mediante el acceso a las propiedades y funciones de los objetos.

### <a name="types-of-automation-clients"></a>Tipos de clientes de automatización

Hay dos tipos de clientes de automatización:

- Los clientes que dinámicamente (en tiempo de ejecución) adquieren información sobre las propiedades y las operaciones del servidor.

- Clientes que poseen información estática (proporcionada en tiempo de compilación) que especifica las propiedades y las operaciones del servidor.

Los clientes del primer tipo adquieren información sobre los métodos y las propiedades del servidor mediante una consulta al mecanismo del sistema OLE `IDispatch` . Aunque es adecuado usar para clientes dinámicos, `IDispatch` es difícil de usar para clientes estáticos, donde los objetos que se van a controlar deben conocerse en tiempo de compilación. En el caso de los clientes enlazados estáticos, Microsoft Foundation Classes proporciona la clase [COleDispatchDriver](reference/coledispatchdriver-class.md) .

Los clientes enlazados estáticos utilizan una clase de proxy vinculada estáticamente a la aplicación cliente. Esta clase proporciona una encapsulación de C++ con seguridad de tipos de las propiedades y las operaciones de la aplicación de servidor.

La clase `COleDispatchDriver` proporciona la compatibilidad principal para el lado cliente de la automatización. Mediante el cuadro de diálogo **Agregar nuevo elemento** , se crea una clase derivada de `COleDispatchDriver` .

A continuación, especifique el archivo de biblioteca de tipos que describe las propiedades y funciones del objeto de la aplicación de servidor. El cuadro de diálogo Agregar elemento Lee este archivo y crea la `COleDispatchDriver` clase derivada de, con las funciones miembro a las que la aplicación puede llamar para tener acceso a los objetos de la aplicación de servidor en C++ de una manera con seguridad de tipos. La funcionalidad adicional heredada de `COleDispatchDriver` simplifica el proceso de llamada al servidor de automatización adecuado.

### <a name="handling-events-in-automation-clients"></a>Controlar eventos en clientes de Automation

Si desea controlar eventos en el cliente de automatización, debe agregar una interfaz de receptor. MFC proporciona compatibilidad con el Asistente para agregar interfaces de receptor para controles ActiveX, pero no para otros servidores COM.

## <a name="see-also"></a>Consulte también

[Clientes de Automation: Usar bibliotecas de tipos](automation-clients-using-type-libraries.md)<br/>
[Automation](automation.md)<br/>
[Asistente para aplicaciones MFC](reference/mfc-application-wizard.md)
