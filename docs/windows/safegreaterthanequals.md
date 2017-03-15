---
title: "SafeGreaterThanEquals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeGreaterThanEquals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeGreaterThanEquals (función)"
ms.assetid: 43312fa9-d925-4f9f-a352-a190c02b3005
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# SafeGreaterThanEquals
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Compara dos números.  
  
## Sintaxis  
  
```  
template <typename T, typename U>  
inline bool SafeGreaterThanEquals (  
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
 `true` si es `t` mayor o igual `u`; si no `false`.  
  
## Comentarios  
 `SafeGreaterThanEquals` mejora el operador de comparación estándar porque permite comparar dos tipos diferentes de números.  
  
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
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeLessThan](../windows/safelessthan.md)