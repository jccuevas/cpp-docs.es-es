---
title: "Platform::ArrayReference (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ArrayReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::ArrayReference (Clase)"
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::ArrayReference (Clase)
`ArrayReference` es un tipo de optimización que puedes usar en lugar de [Platform::Array^](../cppcx/platform-array-class.md) en parámetros de entrada cuando desees rellenar una matriz de estilo C con los datos de entrada.  
  
## Sintaxis  
  
```vb  
  
```  
  
```csharp  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[ArrayReference::ArrayReference \(Constructor\)](../cppcx/arrayreference-arrayreference-constructor.md)|Inicializa una nueva instancia de la clase `ArrayReference`.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Operador ArrayReference::operator\(\)](../cppcx/arrayreference-operator-call-operator.md)|Convierte este `ArrayReference` en `Platform::Array<T>^*`.|  
|[ArrayReference::operator\= \(Operador\)](../cppcx/arrayreference-operator-assign-operator.md)|Asigna el contenido de otro `ArrayReference` a esta instancia.|  
  
## Excepciones  
  
## Comentarios  
 Si usas `ArrayReference` para rellenar una matriz de estilo C, evitas la operación de copia adicional que sería necesaria para copiar primero a una variable `Platform::Array` y después a la matriz de estilo C. Cuando usas `ArrayReference`, solo se realiza una operación de copia. Para obtener un ejemplo de código, vea [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Encabezado de la subsección  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)