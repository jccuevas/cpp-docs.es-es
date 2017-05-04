---
title: "Platform::Exception (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Exception (Clase)"
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Exception (Clase)
Representa los errores que se producen durante la ejecución de una aplicación. Las clases de excepción personalizadas no se pueden derivar de `Platform::Exception`. Si necesitas una excepción personalizada, puedes utilizar `Platform::COMException` y especificar un HRESULT específico de la aplicación.  
  
## Sintaxis  
  
```cpp  
public ref class Exception : Object,    IException,    IPrintable,    IEquatable  
```  
  
## Miembros  
 La clase `Exception` hereda de la clase `Object` y las interfaces `IException`, `IPrintable` y `IEquatable`.  
  
 La clase `Exception` también tiene las siguientes clases de miembros.  
  
### Constructores  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[Exception::Exception \(Constructor\)](../cppcx/exception-exception-constructor.md)|Inicializa una nueva instancia de la clase `Exception`.|  
  
### Métodos  
 La clase `Exception` hereda los métodos `Equals()`, `Finalize()`, `GetHashCode()`, `GetType()`, `MemberwiseClose()` y `ToString()` de [Platform::Object \(Clase\)](../cppcx/platform-object-class.md). La clase `Exception` también tiene el método siguiente.  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[Exception::CreateException \(Método\)](../cppcx/exception-createexception-method.md)|Crea una excepción que representa el valor HRESULT especificado.|  
  
### Propiedades  
 La clase Exception también tiene las propiedades siguientes.  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[Exception::HResult \(Propiedad\)](../cppcx/exception-hresult-property.md)|HRESULT correspondiente a la excepción.|  
|[Exception::Message \(Propiedad\)](../cppcx/exception-message-property.md)|Un mensaje que describe la excepción. Este valor es de solo lectura y se no puede modificarse después de que se haya generado `Exception`.|  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)