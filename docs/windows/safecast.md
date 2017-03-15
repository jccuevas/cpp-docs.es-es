---
title: "SafeCast | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeCast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeCast (función)"
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# SafeCast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Conversiones de un tipo de número a otro tipo.  
  
## Sintaxis  
  
```  
template<typename T, typename U>  
inline bool SafeCast (  
   const T From,  
   U& To  
);  
```  
  
#### Parámetros  
 \[in\] `From`  
 El número de origen que se va a convertir.  Esto debe ser de tipo t.  
  
 \[out\] `To`  
 Una referencia al nuevo tipo de número.  Esto debe ser de tipo U.  
  
## Valor devuelto  
 `true` si no se produce ningún error; `false` si se produce un error.  
  
## Comentarios  
 Este método forma parte de [SafeInt \(Biblioteca\)](../windows/safeint-library.md) y está diseñado para una sola colada sin crear una instancia de [SafeInt \(Clase\)](../windows/safeint-class.md).  
  
> [!NOTE]
>  Este método debe utilizarse únicamente cuando una sola operación debe proteger.  Si hay varias operaciones, debe usar la clase de `SafeInt` en lugar de llamar a funciones independientes individuales.  
  
 Para obtener más información sobre los tipos t de plantilla y el U, vea [SafeInt \(Funciones\)](../windows/safeint-functions.md).  
  
## Requisitos  
 **Encabezado:** safeint.h  
  
 **Espacio de nombres:** Microsoft::Utilities  
  
## Vea también  
 [SafeInt \(Funciones\)](../windows/safeint-functions.md)   
 [SafeInt \(Biblioteca\)](../windows/safeint-library.md)   
 [SafeInt \(Clase\)](../windows/safeint-class.md)