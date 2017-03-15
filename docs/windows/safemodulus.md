---
title: "SafeModulus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeModulus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeModulus (función)"
ms.assetid: ae5c81eb-5dcf-45a5-aa76-465fdfe68654
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# SafeModulus
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Realiza la operación de módulo en dos números.  
  
## Sintaxis  
  
```  
template<typename T, typename U>  
inline bool SafeModulus (  
   const T t,  
   const U u,  
   T& result  
) throw ();  
```  
  
#### Parámetros  
 \[in\] `t`  
 Divisor.  Esto debe ser de tipo t.  
  
 \[in\] `u`  
 Dividendo.  Esto debe ser de tipo U.  
  
 \[out\] `result`  
 El parámetro donde `SafeModulus` almacena el resultado.  
  
## Valor devuelto  
 `true` si no se produce ningún error; `false` si se produce un error.  
  
## Comentarios  
 Este método forma parte de [SafeInt \(Biblioteca\)](../windows/safeint-library.md) y está diseñado para una única operación de módulo sin crear una instancia de [SafeInt \(Clase\)](../windows/safeint-class.md).  
  
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
 [SafeDivide](../windows/safedivide.md)