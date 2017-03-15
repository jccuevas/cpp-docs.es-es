---
title: "HStringReference::HStringReference (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference"
dev_langs: 
  - "C++"
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# HStringReference::HStringReference (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase HStringReference.  
  
## Sintaxis  
  
```cpp  
  
    template<unsigned int sizeDest>  
    HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
    template<unsigned int sizeDest>  
    HStringReference(wchar_t const (&str)[ sizeDest],   
unsigned int len)  
       throw();  
  
    HStringReference(HStringReference&& other) throw();  
  
```  
  
#### Parámetros  
 `sizeDest`  
 Un parámetro de plantilla que especifica el tamaño del búfer de HStringReference de destino.  
  
 `str`  
 Una referencia a una cadena de caracteres.  
  
 `len`  
 La longitud máxima del búfer del parámetro de `str` a usar en esta operación.  Si el parámetro de `len` no se especifica, se utiliza el parámetro completo de `str` .  Si `len` es mayor que `sizeDest`, `len` se establece en `sizeDest`\-1.  
  
 `other`  
 Otro objeto de HStringReference.  
  
## Comentarios  
 El primer constructor inicializa un nuevo objeto de HStringReference que el mismo tamaño como parámetro `str`.  
  
 El segundo constructor inicializa un nuevo objeto de HStringReference que el specifeid de tamaño por el parámetro `len`.  
  
 El tercer constructor inicializa un nuevo objeto de HStringReference en el valor del parámetro de `other`, y después destruye el parámetro de `other` .  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [HStringReference \(Clase\)](../windows/hstringreference-class.md)