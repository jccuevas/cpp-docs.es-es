---
title: Los clientes de automatización | Documentos de Microsoft
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
ms.openlocfilehash: a29b11028df84a7e5e67adb7588386f77adcff06
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929044"
---
# <a name="automation-clients"></a>clientes de automatización
Automatización permite a la aplicación para manipular objetos implementados en otra aplicación o exponga objetos para que se puedan manipular. Un cliente de automatización es una aplicación que puede manipular objetos expuestos por otra aplicación. La aplicación que expone los objetos se denomina servidor de automatización. El cliente usa los objetos de la aplicación de servidor mediante el acceso a funciones y propiedades de esos objetos.  
  
### <a name="types-of-automation-clients"></a>Tipos de clientes de automatización  
 Hay dos tipos de clientes de automatización:  
  
-   Clientes que dinámicamente (en tiempo de ejecución) para obtener información acerca de las propiedades y las operaciones del servidor.  
  
-   Clientes que poseen información estática (proporcionada en tiempo de compilación) que especifica las propiedades y las operaciones del servidor.  
  
 Los clientes del primer tipo obtienen información sobre los métodos y propiedades del servidor al consultar el sistema OLE `IDispatch` mecanismo. Aunque resulta adecuada que se usará para clientes dinámicos, `IDispatch` es difícil de usar para clientes estáticos, donde los objetos se controla debe conocerse en tiempo de compilación. Para estático enlazado a los clientes, Microsoft Foundation classes proporcionan el [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) clase.  
  
 Clientes enlazados estáticos utilizan una clase de proxy que está vinculada estáticamente con la aplicación cliente. Esta clase proporciona una encapsulación de C++ con seguridad de tipos de operaciones y las propiedades de la aplicación de servidor.  
  
 La clase `COleDispatchDriver` proporciona el soporte técnico principal para el cliente de automatización. Mediante el **Agregar nuevo elemento** cuadro de diálogo, se creará una clase derivada de `COleDispatchDriver`.  
  
 A continuación, especifique el archivo de biblioteca de tipos que describe las propiedades y funciones del objeto de la aplicación de servidor. El cuadro de diálogo Agregar elemento leerá este archivo y crea el `COleDispatchDriver`-clase derivada, con funciones miembro que la aplicación puede llamar para obtener acceso a objetos de la aplicación de servidor en C++ de una manera de seguridad de tipos. Funcionalidad adicional que se hereda de `COleDispatchDriver` simplifica el proceso de llamada al servidor de automatización adecuado.  
  
### <a name="handling-events-in-automation-clients"></a>Control de eventos en los clientes de automatización  
 Si desea controlar los eventos en el cliente de automatización, debe agregar una interfaz de receptor. MFC proporciona compatibilidad de Asistente para agregar las interfaces de receptor para controles ActiveX, pero no se admite para los otros servidores COM. Para obtener información sobre cómo agregar una interfaz de receptor en un cliente MFC para las interfaces de origen descrito por los servidores COM, vea Cómo: crear una interfaz de receptor en el cliente de COM MFC-Based (KB 181845) en [ http://support.microsoft.com/default.aspxscid=kb; en-us; 181845](http://support.microsoft.com/default.aspxscid=kb;en-us;181845).  
  
## <a name="see-also"></a>Vea también  
 [Los clientes de automatización: Usar bibliotecas de tipos](../mfc/automation-clients-using-type-libraries.md)   
 [Automatización](../mfc/automation.md)   
 [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md)

