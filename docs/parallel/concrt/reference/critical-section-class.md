---
title: "critical_section (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::critical_section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "critical_section (clase)"
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# critical_section (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una exclusión mutua no reentrante que es explícitamente consciente del runtime de simultaneidad.  
  
## Sintaxis  
  
```  
class critical_section;  
```  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`native_handle_type`|Una referencia a un objeto `critical_section`.|  
  
### Clases públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[critical\_section::scoped\_lock \(Clase\)](../Topic/critical_section::scoped_lock%20Class.md)|Una excepción segura del contenedor RAII para un objeto `critical_section`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[critical\_section::critical\_section \(Constructor\)](../Topic/critical_section::critical_section%20Constructor.md)|Construye una nueva sección crítica.|  
|[critical\_section::~critical\_section \(Destructor\)](../Topic/critical_section::~critical_section%20Destructor.md)|Destruye una sección crítica.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[critical\_section::lock \(Método\)](../Topic/critical_section::lock%20Method.md)|Adquiere esta sección crítica.|  
|[critical\_section::native\_handle \(Método\)](../Topic/critical_section::native_handle%20Method.md)|Devuelve un identificador nativo específico de la plataforma, si existe alguno.|  
|[critical\_section::try\_lock \(Método\)](../Topic/critical_section::try_lock%20Method.md)|Intenta adquirir el bloqueo sin bloquearse.|  
|[critical\_section::try\_lock\_for \(Método\)](../Topic/critical_section::try_lock_for%20Method.md)|Intenta adquirir el bloqueo sin bloquear para un número concreto de milisegundos.|  
|[critical\_section::unlock \(Método\)](../Topic/critical_section::unlock%20Method.md)|Desbloquea la sección crítica.|  
  
## Comentarios  
 Para obtener más información, vea [Estructuras de datos de sincronización](../../../parallel/concrt/synchronization-data-structures.md).  
  
## Jerarquía de herencia  
 `critical_section`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [reader\_writer\_lock \(Clase\)](../../../parallel/concrt/reference/reader-writer-lock-class.md)