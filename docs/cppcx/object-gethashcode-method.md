---
title: "Object::GetHashCode (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::GetHashCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Plataforma, Object::GetHashCode"
ms.assetid: 403a60e9-be1d-4702-b14d-27fa4b2a043b
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::GetHashCode (M&#233;todo)
Devuelve el valor de identidad [IUnknown](../atl/iunknown.md)\* para esta instancia si es un objeto COM o un valor hash calculado si no es un objeto COM.  
  
## Sintaxis  
  
```cpp  
public:int GetHashCode()  
```  
  
## Valor devuelto  
 Valor numérico que identifica de forma única este objeto.  
  
## Comentarios  
 Puedes usar GetHashCode para crear claves para objetos de mapas. Puedes comparar códigos hash mediante [Object::Equals \(Método\)](../cppcx/object-equals-method.md). Si la ruta de acceso del código es sumamente crítica y `GetHashCode` y `Equals` no son suficientemente rápidos, puedes bajar hasta el nivel COM subyacente y realizar comparaciones de puntero de [IUnknown](../atl/iunknown.md) nativo.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::Object \(Clase\)](../cppcx/platform-object-class.md)