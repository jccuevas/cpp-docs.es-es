---
title: "SafeLessThan | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeLessThan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeLessThan (función)"
ms.assetid: 9d85bc0d-8d94-4d59-9b72-ef3c63a120a0
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# SafeLessThan
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Determina si un número es menor que otro.  
  
## Sintaxis  
  
```  
template<typename T, typename U>  
inline bool SafeLessThan (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### Parámetros  
 \[in\] `t`  
 El primer número.  Esto debe ser de tipo t.  
  
 \[in\] `u`  
 El segundo numer.  Esto debe ser de tipo U.  
  
## Valor devuelto  
 `true` si `t` es menor que `u`; si no `false`.  
  
## Comentarios  
 Este método mejora el operador de comparación estándar porque `SafeLessThan` permite comparar dos tipos diferentes de número.  
  
 Este método forma parte de [SafeInt \(Biblioteca\)](../windows/safeint-library.md) y está diseñado para una única operación de comparación sin crear una instancia de [SafeInt \(Clase\)](../windows/safeint-class.md).  
  
> [!NOTE]
>  Este método debe utilizarse únicamente cuando una sola operación matemática debe proteger.  Si hay varias operaciones, debe usar la clase de `SafeInt` en lugar de llamar a funciones independientes individuales.  
  
 Para obtener más información sobre los tipos t de plantilla y el U, vea [SafeInt \(Funciones\)](../windows/safeint-functions.md).  
  
## Requisitos  
 **Encabezado:** safeint.h  
  
 **Espacio de nombres:** Microsoft::Utilities  
  
## Vea también  
 [SafeInt \(Funciones\)](../windows/safeint-functions.md)   
 [SafeInt \(Biblioteca\)](../windows/safeint-library.md)   
 [SafeInt \(Clase\)](../windows/safeint-class.md)   
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)