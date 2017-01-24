---
title: "runtime_exception (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::direct3d_abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "runtime_exception (clase)"
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# runtime_exception (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

El tipo base para las excepciones en C\+\+ la biblioteca de Paralelismo Masivo Acelerado \(AMP\).  
  
## Sintaxis  
  
```  
class runtime_exception : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[runtime\_exception::runtime\_exception \(Constructor\)](../Topic/runtime_exception::runtime_exception%20Constructor.md)|Inicializa una nueva instancia de la clase `runtime_exception`.|  
|[runtime\_exception::~runtime\_exception \(Destructor\)](../Topic/runtime_exception::~runtime_exception%20Destructor.md)|Destruye el objeto `runtime_exception`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[runtime\_exception::get\_error\_code \(Método\)](../Topic/runtime_exception::get_error_code%20Method.md)|Devuelve el código de error que generó la excepción.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[runtime\_exception::operator\= \(Operador\)](../Topic/runtime_exception::operator=%20Operator.md)|Copia el contenido del objeto especificado `runtime_exception` en este.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `runtime_exception`  
  
## Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)