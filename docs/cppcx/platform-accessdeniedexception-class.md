---
title: "Platform::AccessDeniedException (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::AccessDeniedException"
  - "Platform/Platform::AccessDeniedException::AccessDeniedException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::AccessDeniedException"
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::AccessDeniedException (Clase)
Se produce cuando se deniega el acceso a un recurso o a una característica.  
  
## Sintaxis  
  
```cpp  
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable  
```  
  
## Comentarios  
 Si obtienes esta excepción, asegúrate de que has solicitado la capacidad adecuada y de que has realizado las declaraciones necesarias en el manifiesto del paquete de tu aplicación. Para obtener más información, consulta [Configurar un paquete de la aplicación de Windows 8.1 con el diseñador de manifiestos](http://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d) y la clase [COMException](../cppcx/platform-comexception-class.md).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Platform::COMException \(Clase\)](../cppcx/platform-comexception-class.md)