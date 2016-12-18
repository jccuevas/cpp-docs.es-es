---
title: "HString (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HString"
dev_langs: 
  - "C++"
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona compatibilidad para manipular los identificadores HSTRING.  
  
## Sintaxis  
  
```cpp  
class HString;  
```  
  
## Comentarios  
 El [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] proporciona acceso a las cadenas a través de identificadores de HSTRING.  La clase HString proporciona funciones y operadores de comodidad para simplificar mediante identificadores de HSTRING.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HString::HString \(Constructor\)](../windows/hstring-hstring-constructor.md)|Inicializa una nueva instancia de la clase HString.|  
|[HString::~HString \(Destructor\)](../windows/hstring-tilde-hstring-destructor.md)|Destruye la instancia actual de la clase HString.|  
  
### Miembros  
  
|Name|Descripción|  
|----------|-----------------|  
|[HString::Set \(Método\)](../Topic/HString::Set%20Method.md)|Establece el valor del objeto HString actual en la cadena de caracteres anchos o el parámetro HString especificados.|  
|[HString::Attach \(Método\)](../windows/hstring-attach-method.md)|Asocia el objeto HString especificado al objeto HString actual.|  
|[HString::CopyTo \(Método\)](../windows/hstring-copyto-method.md)|Copia el objeto HString actual a un objeto HSTRING.|  
|[HString::Detach \(Método\)](../Topic/HString::Detach%20Method.md)|Desasocia el objeto especificado de HString de su valor subyacente.|  
|[HString::GetAddressOf \(Método\)](../windows/hstring-getaddressof-method.md)|Recupera un puntero al identificador HSTRING subyacente.|  
|[HString::Get \(Método\)](../Topic/HString::Get%20Method.md)|Recupera el valor del identificador HSTRING subyacente.|  
|[HString::Release \(Método\)](../windows/hstring-release-method.md)|Elimina el valor de cadena subyacente e inicializa el objeto HString actual con un valor vacío.|  
|[HString::MakeReference \(Método\)](../Topic/HString::MakeReference%20Method.md)|Crea un objeto HStringReference a partir de un parámetro de cadena específico.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HString::Operator\= \(Operador\)](../Topic/HString::Operator=%20Operator.md)|Mueve el valor de otro objeto HString al objeto HString actual.|  
|[HString::Operator\=\= \(Operador\)](../windows/hstring-operator-equality-operator.md)|Indica si los dos parámetros son iguales.|  
|[HString::Operator\!\= \(Operador\)](../windows/hstring-operator-inequality-operator.md)|Indica si los dos parámetros no son iguales.|  
  
## Jerarquía de herencia  
 `HString`  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [Microsoft::WRL::Wrappers \(Espacio de nombres\)](../Topic/Microsoft::WRL::Wrappers%20Namespace.md)