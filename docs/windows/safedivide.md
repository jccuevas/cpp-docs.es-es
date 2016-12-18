---
title: "SafeDivide | Microsoft Docs"
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
  - "SafeDivide"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeDivide (función)"
ms.assetid: b5b27484-ad6e-46b1-ba9f-1c7120dd103b
caps.latest.revision: 5
caps.handback.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeDivide
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Divide dos números de manera que protege contra dividir por cero.  
  
## Sintaxis  
  
```  
template<typename T, typename U>  
inline bool SafeDivide (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### Parámetros  
 \[in\] `t`  
 Divisor.  Esto debe ser de tipo t.  
  
 \[in\] `u`  
 Dividendo.  Esto debe ser de tipo U.  
  
 \[out\] `result`  
 El parámetro donde `SafeDivide` almacena el resultado.  
  
## Valor devuelto  
 `true` si no se produce ningún error; `false` si se produce un error.  
  
## Comentarios  
 Este método forma parte de [SafeInt \(Biblioteca\)](../windows/safeint-library.md) y está diseñado para una única operación de división sin crear una instancia de [SafeInt \(Clase\)](../windows/safeint-class.md).  
  
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
 [SafeModulus](../windows/safemodulus.md)   
 [SafeMultiply](../Topic/SafeMultiply.md)