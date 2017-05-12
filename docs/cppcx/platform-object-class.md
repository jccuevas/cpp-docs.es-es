---
title: "Platform::Object (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Object (clase)"
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Platform::Object (Clase)
Proporciona un comportamiento común para clases ref y structs ref en aplicaciones de la Tienda Windows. Todas las instancias de clase ref y struct ref se pueden convertir implícitamente a Platform::Object^ y pueden invalidar su método ToString virtual.  
  
## Sintaxis  
  
```scr  
public ref class Object : Object  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Object::Object \(Constructor\)](../cppcx/object-object-constructor.md)|Inicializa una nueva instancia de la clase Object.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Object::Equals \(Método\)](../cppcx/object-equals-method.md)|Determina si el objeto especificado es igual al objeto actual.|  
|[Object::GetHashCode \(Método\)](../cppcx/object-gethashcode-method.md)|Devuelve el código hash de esta instancia.|  
|[Object::ReferenceEquals \(Método\)](../cppcx/object-referenceequals-method.md)|Determina si las instancias de Object especificadas son la misma instancia.|  
|[ToString \(método\)](../cppcx/object-tostring-method-c-cx.md)|Devuelve una cadena que representa el objeto actual. Puede invalidarse.|  
|[GetType \(Método\)](../cppcx/object-gettype-method.md)|Obtiene un [Platform::Type](../cppcx/platform-type-class.md) que describe la instancia actual.|  
  
## Jerarquía de herencia  
 `Object`  
  
 `Object`  
  
## Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Plataforma  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)