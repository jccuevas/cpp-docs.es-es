---
title: "HStringReference (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference"
dev_langs: 
  - "C++"
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HStringReference (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un objeto HSTRING que se crea a partir de una cadena existente.  
  
## Sintaxis  
  
```cpp  
class HStringReference;  
```  
  
## Comentarios  
 La duración del búfer de respaldo en la nueva HSTRING no está administrada por [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  El llamador asigna una cadena de origen en el marco de pila para evitar una asignación de pila y eliminar el riesgo de una pérdida de memoria.  Además, el llamador debe asegurarse de que no se modifica la cadena de origen durante la duración de HSTRING adjunto.  Para obtener más información, vea [WindowsCreateStringReference function](http://msdn.microsoft.com/es-es/0361bb7e-da49-4289-a93e-de7aab8712ac).  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HStringReference::HStringReference \(Constructor\)](../windows/hstringreference-hstringreference-constructor.md)|Inicializa una nueva instancia de la clase HStringReference.|  
  
### Miembros  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|[HStringReference::CopyTo \(Método\)](../windows/hstringreference-copyto-method.md)|Copia el objeto HStringReference actual a un objeto HSTRING.|  
|[HStringReference::Get \(Método\)](../windows/hstringreference-get-method.md)|Recupera el valor del identificador HSTRING subyacente.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HStringReference::Operator\= \(Operador\)](../windows/hstringreference-operator-assign-operator.md)|Mueve el valor de otro objeto HStringReference al objeto HStringReference actual.|  
|[HStringReference::Operator\=\= \(Operador\)](../windows/hstringreference-operator-equality-operator.md)|Indica si los dos parámetros son iguales.|  
|[HStringReference::Operator\!\= \(Operador\)](../windows/hstringreference-operator-inequality-operator.md)|Indica si los dos parámetros no son iguales.|  
  
## Jerarquía de herencia  
 `HStringReference`  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [Microsoft::WRL::Wrappers \(Espacio de nombres\)](../Topic/Microsoft::WRL::Wrappers%20Namespace.md)