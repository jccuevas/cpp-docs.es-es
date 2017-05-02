---
title: "Agile::Agile (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::Agile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::Agile"
ms.assetid: 33c1df82-f5db-4750-98cc-0daa03be4e59
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::Agile (Constructor)
Inicializa una nueva instancia de la clase Agile.  
  
## Sintaxis  
  
```cpp  
  
 Agile();  
  
Agile(T^ object);   
  
Agile(const Agile<T>& object);  
  
Agile(Agile<T>&& object);  
  
```  
  
#### Parámetros  
 `T`  
 Un tipo especificado por el parámetro typename de la plantilla.  
  
 `object`  
 En la segunda versión de este constructor, un objeto utilizado para inicializar una nueva instancia de Agile. En la tercera versión, el objeto que se copia en la nueva instancia de Agile. En la cuarta versión, el objeto que se mueve a la nueva instancia de Agile.  
  
## Comentarios  
 La primera versión de este constructor es el constructor predeterminado. La segunda versión inicializa una nueva clase de instancia de Agile del objeto especificado por el parámetro `object`. La tercera versión es el constructor de copias. La cuarta versión es el constructor de movimiento. Este constructor no puede producir excepciones.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::Agile \(Clase\)](../cppcx/platform-agile-class.md)