---
title: "SafeLessThanEquals | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeLessThanEquals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeLessThanEquals (función)"
ms.assetid: cbd70526-faf2-4fbc-96a0-b61e8cf5f04a
caps.latest.revision: 6
caps.handback.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeLessThanEquals
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Compara dos números.  
  
## Sintaxis  
  
```  
template <typename T, typename U>  
inline bool SafeLessThanEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### Parámetros  
 \[in\] `t`  
 Primer número que se va a comparar.  Esto debe ser de tipo t.  
  
 \[in\] `u`  
 Segundo número que se va a comparar.  Esto debe ser de tipo U.  
  
## Valor devuelto  
 `true` si es `t` menor o igual que `u`; si no `false`.  
  
## Comentarios  
 `SafeLessThanEquals` extiende el operador de comparación regular la funcionalidad para comparar dos tipos diferentes de números.  
  
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
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeLessThan](../windows/safelessthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)