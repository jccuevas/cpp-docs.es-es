---
title: "WeakReference (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::WeakReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakReference (clase)"
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakReference (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
class WeakReference;  
```  
  
## Comentarios  
 Representa *una referencia parcial* que se puede usar con el tiempo de ejecución o el trabajo clásica COM de Windows.  Una referencia parcial representa un objeto que puede o no ser accesible.  
  
 Un objeto de `WeakReference` mantiene *una referencia segura*, que es un puntero a un objeto, y *un recuento fundamental de referencia*, que es el número de copias de la referencia segura que han sido distribuidas por el método de Resolve\(\).  Mientras el recuento fundamental de la referencia es cero, la referencia segura es válida y el objeto es alcanzable.  Cuando el número de tipos de referencia se convierte en cero, la referencia segura no es válida y el objeto es inaccesible.  
  
 Un objeto de WeakReference se utiliza normalmente para representar un objeto cuya existencia está controlada por un subproceso o una aplicación externo.  Por ejemplo, cree un objeto de WeakReference de una referencia a un objeto de archivo.  Mientras el archivo abierto, la referencia segura es válida.  Pero si se cierra el archivo, la referencia segura deja de ser válida.  
  
 Los métodos de WeakReference son seguros para subprocesos.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[WeakReference::WeakReference \(Constructor\)](../windows/weakreference-weakreference-constructor.md)|Inicializa una nueva instancia de la clase de WeakReference.|  
|[WeakReference::~WeakReference \(Destructor\)](../windows/weakreference-tilde-weakreference-destructor.md)|Desinicializa \(destruye\) de la instancia actual de la clase de WeakReference.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference \(Método\)](../Topic/WeakReference::DecrementStrongReference%20Method.md)|Disminuye el recuento fundamental de la referencia de objeto actual de WeakReference.|  
|[WeakReference::IncrementStrongReference \(Método\)](../windows/weakreference-incrementstrongreference-method.md)|Incrementa el recuento fundamental de la referencia de objeto actual de WeakReference.|  
|[WeakReference::Resolve \(Método\)](../windows/weakreference-resolve-method.md)|Establece el puntero especificado en el valor de referencia segura actual si el recuento de referencia es distinto de cero.|  
|[WeakReference::SetUnknown \(Método\)](../windows/weakreference-setunknown-method.md)|Establece la referencia segura del objeto actual de WeakReference el puntero de interfaz especificado.|  
  
## Jerarquía de herencia  
 `WeakReference`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)