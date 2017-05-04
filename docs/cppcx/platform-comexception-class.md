---
title: "Platform::COMException (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::COMException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::COMException (Clase)"
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::COMException (Clase)
Representa los errores COM que se producen durante la ejecución de una aplicación. COMException es la clase base para un conjunto de excepciones estándar predefinidas.  
  
## Sintaxis  
  
```cpp  
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable  
```  
  
## Miembros  
 La clase COMException hereda de la clase Object y las interfaces IException, IPrintable e IEquatable.  
  
 COMException también tiene los siguientes tipos de miembros.  
  
 **Constructores**  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|`COMException`|Inicializa una nueva instancia de la clase COMException.|  
  
 **Métodos**  
  
 La clase COMException hereda los métodos Equals\(\), Finalize\(\), GetHashCode\(\), GetType\(\), MemberwiseClose\(\) y ToString\(\) de [Platform::Object \(Clase\)](../cppcx/platform-object-class.md).  
  
 **Propiedades**  
  
 La clase COMException tiene las propiedades siguientes.  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[Exception::HResult \(Propiedad\)](../cppcx/exception-hresult-property.md)|HRESULT correspondiente a la excepción.|  
|[Exception::Message \(Propiedad\)](../cppcx/exception-message-property.md)|Mensaje que describe la excepción.|  
  
## Excepciones derivadas  
 Las excepciones predefinidas siguientes se derivan de COMException. Difieren de COMException únicamente en su nombre, el nombre de su constructor y el valor HRESULT subyacente.  
  
|Nombre|HRESULT subyacente|Descripción|  
|------------|------------------------|-----------------|  
|COMException|*hresult definido por el usuario*|Se produce cuando se devuelve un HRESULT no reconocido de una llamada al método COM.|  
|AccessDeniedException|E\_ACCESSDENIED|Se produce cuando se deniega el acceso a un recurso o a una característica.|  
|ChangedStateException|E\_CHANGED\_STATE|Se produce cuando los métodos de un iterador de colección o de una vista de colección se invocan después de que la colección principal haya cambiado, invalidando los resultados del método.|  
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|Se produce cuando una clase COM no se ha registrado.|  
|DisconnectedException|RPC\_E\_DISCONNECTED|Se produce cuando un objeto se desconecta de sus clientes.|  
|FailureException|E\_FAIL|Se produce cuando una operación no es correcta.|  
|InvalidArgumentException|E\_INVALIDARG|Se produce cuando uno de los argumentos proporcionados a un método no es válido.|  
|InvalidCastException|E\_NOINTERFACE|Se produce cuando un tipo no puede convertirse a otro tipo.|  
|NotImplementedException|E\_NOTIMPL|Se produce si un método de interfaz no se ha implementado en una clase.|  
|NullReferenceException|E\_POINTER|Se produce cuando se intenta desreferenciar una referencia de un objeto null.|  
|OperationCanceledException|E\_ABORT|Se produce cuando se anula una operación.|  
|OutOfBoundsException|E\_BOUNDS|Se produce cuando una operación intenta tener acceso a datos que están fuera del intervalo válido.|  
|OutOfMemoryException|E\_OUTOFMEMORY|Se produce cuando la memoria es insuficiente para completar la operación.|  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)