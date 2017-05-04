---
title: "Platform::IBox (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IBox"
dev_langs: 
  - "C++"
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::IBox (Interfaz)
La interfaz [Platform::IBox](../cppcx/platform-ibox-interface.md) es el nombre de C\+\+ para la interfaz `Windows::Foundation::IReference`.  
  
## Sintaxis  
  
```cpp  
template <typename T>  
interface class IBox  
```  
  
#### Parámetros  
 `T`  
 Tipo del valor al que se le ha aplicado la conversión boxing.  
  
## Comentarios  
 La interfaz `IBox<T>` se usa principalmente para representar tipos de valor que aceptan valores NULL, tal y como se describe en [Clases y structs de valor \(C\+\+\/CX\)](../cppcx/value-classes-and-structs-c-cx.md). La interfaz también se usa internamente para aplicar la conversión boxing a tipos de valor que se pasan a métodos de C\+\+ que toman parámetros de tipo `Object^`. Puedes declarar explícitamente un parámetro de entrada como `IBox<SomeValueType>`. Para obtener un ejemplo, consulta [Conversión boxing](../cppcx/boxing-c-cx.md).  
  
## Requisitos  
  
## Miembros  
 La interfaz `Platform::IBox` hereda de la interfaz [Platform::IValueType](../cppcx/platform-ivaluetype-interface.md).`IBox` tiene estos miembros:  
  
 **Propiedades**  
  
|Método|Descripción|  
|------------|-----------------|  
|Valor|Devuelve el valor al que se le ha aplicado la conversión unboxing y que se almacenó previamente en esta instancia de `IBox`.|  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)