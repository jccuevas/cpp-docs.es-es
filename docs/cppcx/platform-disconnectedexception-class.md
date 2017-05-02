---
title: "Platform::DisconnectedException (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::DisconnectedException"
  - "Platform/Platform::DisconnectedException::DisconnectedException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::DisconnectedException"
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::DisconnectedException (Clase)
Se produce cuando un objeto de proxy COM intenta hacer referencia a un servidor COM que ya no existe.  
  
## Sintaxis  
  
```  
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
## Comentarios  
 Cuando la clase A hace referencia a otra clase \(clase B\) que está en un proceso independiente, la clase A requiere un objeto de proxy para comunicarse con el servidor COM fuera de proceso que contiene la clase B. A veces se puede agotar la memoria del servidor sin que la clase A lo sepa. En ese caso, se produce la excepción RPC\_E\_DISCONNECTED y se convierte a Platform::DisconnectedException. Un escenario en el que se produce consiste en un origen de eventos que invoca un delegado transferido, pero el delegado se destruye en algún punto después de suscribirse al evento. Cuando esto ocurre, el origen de eventos elimina el delegado de la lista de invocación.  
  
 Para obtener más información, consulta la clase [COMException](../cppcx/platform-comexception-class.md).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Platform::COMException \(Clase\)](../cppcx/platform-comexception-class.md)