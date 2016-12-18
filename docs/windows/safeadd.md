---
title: "SafeAdd | Microsoft Docs"
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
  - "SafeAdd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeAdd (función)"
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
caps.latest.revision: 5
caps.handback.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeAdd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Suma dos números de manera que protege contra el desbordamiento.  
  
## Sintaxis  
  
```  
template<typename T, typename U>  
inline bool SafeAdd (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### Parámetros  
 \[in\] `t`  
 El primer número a agregar.  Esto debe ser de tipo t.  
  
 \[in\] `u`  
 El segundo número a agregar.  Esto debe ser de tipo U.  
  
 \[out\] `result`  
 El parámetro donde `SafeAdd` almacena el resultado.  
  
## Valor devuelto  
 `true` si no se produce ningún error; `false` si se produce un error.  
  
## Comentarios  
 Este método forma parte de [SafeInt \(Biblioteca\)](../windows/safeint-library.md) y está diseñado para una única operación de adición sin crear una instancia de [SafeInt \(Clase\)](../windows/safeint-class.md).  
  
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
 [SafeSubtract](../windows/safesubtract.md)