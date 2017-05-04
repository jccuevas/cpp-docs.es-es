---
title: "Platform::StringReference (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::StringReference"
dev_langs: 
  - "C++"
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::StringReference (Clase)
Tipo de optimización que puedes usar para pasar datos de tipo String desde parámetros de entrada `Platform::String^` a otros métodos con un mínimo de operaciones de copia.  
  
## Sintaxis  
  
```cpp  
class StringReference  
```  
  
## Comentarios  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[StringReference::StringReference \(Constructor\)](../cppcx/stringreference-stringreference-constructor.md)|Dos constructores para crear instancias de `StringReference`.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[StringReference::Data \(Método\)](../cppcx/stringreference-data-method.md)|Devuelve los datos de tipo String como una matriz de valores char16.|  
|[StringReference::Length \(Método\)](../cppcx/stringreference-length-method.md)|Devuelve el número de caracteres de la cadena.|  
|[StringReference::GetHSTRING \(Método\)](../cppcx/stringreference-gethstring-method.md)|Devuelve los datos de tipo String como HSTRING.|  
|[StringReference::GetString \(Método\)](../cppcx/stringreference-getstring-method.md)|Devuelve los datos de tipo String como `Platform::String^`.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`StringReference::operator=`|Asigna `StringReference` a una nueva instancia de `StringReference`.|  
|`StringReference::operator()`|Convierte `StringReference` en `Platform::String^`.|  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::StringReference Class](../cppcx/platform-stringreference-class.md)