---
title: "Platform::WeakReference (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform::WeakReference"
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::WeakReference (Clase)
Representa una referencia débil a una instancia de una clase ref.  
  
## Sintaxis  
  
```vb  
class WeakReference  
```  
  
#### Parámetros  
  
## Miembros  
  
### Constructores  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[WeakReference::WeakReference \(Constructor\)](../cppcx/weakreference-weakreference-constructor-c-cx.md)|Inicializa una nueva instancia de la clase WeakReference.|  
  
### Métodos  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[WeakReference::Resolve \(Método\)](../cppcx/weakreference-resolve-method-platform-namespace.md)|Devuelve un identificador a la clase ref subyacente o nullptr si el objeto ya no existe.|  
  
### Operadores  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[WeakReference::operator\=](../cppcx/weakreference-operator-assign.md)|Asigna un nuevo valor al objeto WeakReference.|  
  
## Comentarios  
 La clase WeakReference no es una clase ref y, por tanto, no hereda de Platform::Object^ y no se puede usar en la firma de un método público.  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)