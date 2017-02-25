---
title: "Implementing a Dual Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces duales, implementar"
  - "IDispatchImpl (clase), implementing dual interfaces"
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Implementing a Dual Interface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede implementar una interfaz dual mediante la clase de [IDispatchImpl](../atl/reference/idispatchimpl-class.md) , que proporciona una implementación predeterminada de los métodos de `IDispatch` en una interfaz dual.  Para obtener más información, vea [Implementing the IDispatch Interface](http://msdn.microsoft.com/es-es/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
 para utilizar esta clase:  
  
-   Define la interfaz dual en una biblioteca de tipos.  
  
-   Derive la clase de una especialización de `IDispatchImpl` \(información de paso sobre la interfaz y la biblioteca de tipos como argumentos de plantilla\).  
  
-   Agregue una entrada \(o las entradas\) al mapa COM para exponer la interfaz dual con `QueryInterface`.  
  
-   Implemente la parte vtable de interfaz en la clase.  
  
-   Asegúrese de que la biblioteca de tipos que contiene la definición de interfaz esté disponible para los objetos en tiempo de ejecución.  
  
## Asistente para objetos simples ATL  
 Si desea crear una interfaz y una nueva clase para implementarlo, puede utilizar [ATL agregan el cuadro de diálogo de la clase](../ide/add-class-dialog-box.md)y, a continuación [Asistente para objetos simples ATL](../atl/reference/atl-simple-object-wizard.md).  
  
## Asistente para implementar interfaces  
 Si tiene una interfaz existente, puede utilizar [Asistente para implementar interfaces](../atl/reference/adding-a-new-interface-in-an-atl-project.md) para agregar las entradas necesarias de la clase base, el mapa COM, y las implementaciones de esquemáticas método a una clase existente.  
  
> [!NOTE]
>  Puede ser necesario ajustar la clase base generada para pasar los números de versión principal y secundaria de la biblioteca de tipos como argumentos de plantilla a la clase base de `IDispatchImpl` .  El asistente para implementar interfaces no comprueba el número de versión de la biblioteca de tipos.  
  
## implementar IDispatch  
 Puede utilizar una clase base de `IDispatchImpl` para proporcionar una implementación de dispinterface simplemente especificando la entrada adecuada en el mapa COM \(mediante la macro de [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md) o de [COM\_INTERFACE\_ENTRY\_IID](../Topic/COM_INTERFACE_ENTRY_IID.md) \) siempre que tenga una biblioteca de tipos que describe una interfaz dual correspondiente.  Es muy común implementar la interfaz de `IDispatch` de esta manera, por ejemplo.  El asistente para objetos simples ATL y el asistente ambos de implementar interfaz suponen que piensa implementar `IDispatch` de esta manera, por lo que se agregará la entrada correspondiente al mapa.  
  
> [!NOTE]
>  ATL proporciona clases de [IDispEventImpl](../atl/reference/idispeventimpl-class.md) y de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) para ayudarle dispinterfaces de implementan sin necesidad de una biblioteca de tipos que contiene la definición de una interfaz dual compatible.  
  
## Vea también  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)