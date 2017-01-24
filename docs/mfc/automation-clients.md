---
title: "Clientes de automatizaci&#243;n | Microsoft Docs"
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
  - "clientes de automatización"
  - "clientes"
  - "clientes, automatización"
  - "bibliotecas de tipos, clientes de automatización"
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clientes de automatizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La automatización permite a la aplicación manipular los objetos implementados en otra aplicación, o exponer objetos para que puedan ser manipulados.  Un cliente de automatización es una aplicación que puede manipular los objetos expuestos que pertenecen a otra aplicación.  La aplicación que expone objetos se llama al servidor de automatización.  El cliente manipular los objetos de la aplicación de servidor se obtiene acceso a las propiedades de esos objetos y funciona.  
  
### Tipos de clientes de automatización  
 Hay dos tipos de clientes de automatización:  
  
-   Clientes que dinámicamente \(en tiempo de ejecución\) obtenga información sobre las propiedades y las operaciones del servidor.  
  
-   Clientes que poseen información estática \(proporcionada en tiempo de compilación\) que especifica las propiedades y las operaciones del servidor.  
  
 Los clientes de primera clase adquieren la información sobre los métodos y las propiedades de servidor consultando el mecanismo OLE de `IDispatch` del sistema.  Aunque es adecuado utilizar para los clientes dinámicos, `IDispatch` es difícil de utilizar para los clientes estáticos, donde los objetos que controla deben conocer en tiempo de compilación.  Para los clientes enlazados estáticos, las clases base de Microsoft proporcionan la clase de [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) .  
  
 Los clientes enlazados estáticos utilizan una clase de proxy que se vincule estáticamente a la aplicación cliente.  Esta clase proporciona una encapsulación tipo\-segura de C\+\+ de las propiedades y de las operaciones de la aplicación de servidor.  
  
 La clase `COleDispatchDriver` proporciona compatibilidad principal del cliente de automatización.  Mediante el cuadro de diálogo `Add New Item` , crea una clase derivada de `COleDispatchDriver`.  
  
 A continuación especifica el archivo de biblioteca de tipos que describe las propiedades y las funciones del objeto de la aplicación de servidor.  El cuadro de diálogo agregar elemento lee este archivo y crea `COleDispatchDriver`\- la clase derivada, con las funciones miembro que la aplicación puede llamar para tener acceso a los objetos de la aplicación de servidor en C\+\+ de forma tipo\- segura.  La función adicional heredada de `COleDispatchDriver` simplifica el proceso de llamada al servidor de automatización adecuado.  
  
### Administrar eventos en los clientes de automatización  
 Si desea controlar eventos en el cliente de automatización, necesita agregar una interfaz de receptor.  MFC proporciona compatibilidad del asistente para agregar las interfaces de receptor de controles ActiveX, pero no compatibilidad con otros servidores COM.  Para obtener información sobre cómo agregar una interfaz de receptor en un cliente de MFC para interfaces de origen descritas por los servidores COM, vea HOWTO: Cree una interfaz de receptor en el cliente COM MFC\- basado \(181845 KB\) en [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;181845](http://support.microsoft.com/default.aspx?scid=kb;en-us;181845).  
  
## Vea también  
 [Clientes de automatización: Usar bibliotecas de tipos](../mfc/automation-clients-using-type-libraries.md)   
 [automatización](../mfc/automation.md)   
 [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md)