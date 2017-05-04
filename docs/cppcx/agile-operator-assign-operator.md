---
title: "Agile::operator= (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::operator="
ms.assetid: 2c413bef-f103-4911-afb3-0dac5f6a760e
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::operator= (Operador)
Asigna el objeto especificado al objeto Agile actual.  
  
## Sintaxis  
  
```cpp  
  
   Agile<T> operator=(  
   T^ object  
) throw();  
  
   Agile<T> operator=(  
      const Agile<T>& object  
) throw();  
  
   Agile<T> operator=(  
      Agile<T>&& object  
) throw();  
  
   T^ operator=(  
      IUnknown* lp  
) throw();  
  
```  
  
#### Parámetros  
 `T`  
 Tipo especificado por el nombre de tipo de plantilla.  
  
 `object`  
 Objeto o identificador de un objeto que se copia o se mueve al objeto Agile actual.  
  
 `lp`  
 Puntero de interfaz IUnknown de un objeto.  
  
## Valor devuelto  
 Identificador para un objeto de tipo `T`.  
  
## Comentarios  
 La primera versión del operador de asignación copia un identificador para un tipo de referencia al objeto Agile actual. La segunda versión copia una referencia a un tipo Agile al objeto Agile actual. La tercera versión mueve un tipo Agile al objeto Agile actual. La cuarta versión mueve un puntero a un objeto COM al objeto Agile actual.  
  
 La operación de asignación conserva automáticamente el contexto del objeto Agile actual.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::Agile \(Clase\)](../cppcx/platform-agile-class.md)