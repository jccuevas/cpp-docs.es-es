---
title: "SafeInt::SafeInt | Microsoft Docs"
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
  - "SafeInt::SafeInt"
  - "SafeInt"
  - "SafeInt.SafeInt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeInt (clase), constructor"
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeInt::SafeInt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto `SafeInt`.  
  
## Sintaxis  
  
```  
SafeInt() throw  
  
SafeInt (  
   const T& i  
) throw ()  
  
SafeInt (  
   bool b  
) throw ()  
  
template <typename U>  
SafeInt (  
   const SafeInt <U, E>& u  
)  
  
I template <typename U>  
SafeInt (  
   const U& i  
)  
```  
  
#### Parámetros  
 \[in\] `i`  
 El valor del nuevo objeto de `SafeInt` .  Debería ser un parámetro de t o de U tipo, dependiendo del constructor.  
  
 \[in\] `b`  
 El valor booleano para el nuevo objeto de `SafeInt` .  
  
 \[in\] `u`  
 `SafeInt` de tipo U.  El nuevo objeto de `SafeInt` tendrá el mismo valor que `u`, pero lo de tipo t.  
  
 U  
 El tipo de datos almacenados en `SafeInt`.  Puede ser un booleano, carácter, o tipo entero.  Si es un tipo entero, puede ser con signo o sin signo y estar entre 8 y 64 bits.  
  
## Comentarios  
 Para obtener más información sobre los tipos `T` y `E`de plantilla, vea [SafeInt \(Clase\)](../windows/safeint-class.md).  
  
 El parámetro de entrada para el constructor, `i` o `u`, debe ser un booleano, un carácter, o un tipo entero.  Si es otro tipo de parámetro, la clase de `SafeInt` llama [static\_assert](../cpp/static-assert.md) para indicar un parámetro de entrada no válido.  
  
 Los constructores que usan la plantilla escriba convertirlos de `U` automáticamente que el parámetro de entrada en el tipo especificado por `T`.  La clase de `SafeInt` convierte los datos sin pérdida de datos.  Notifica al controlador de errores `E` si no puede convertir los datos para escribir `T` sin pérdida de datos.  
  
 Si crea `SafeInt` de un parámetro booleano, debe inicializar el valor inmediatamente.  No puede construir `SafeInt` mediante el código `SafeInt<bool> sb;`.  Esto generará un error de compilación.  
  
## Requisitos  
 **Encabezado:** safeint.h  
  
 msl::utilities de**Espacio de nombres:**  
  
## Vea también  
 [SafeInt \(Biblioteca\)](../windows/safeint-library.md)   
 [SafeInt \(Clase\)](../windows/safeint-class.md)   
 [SafeIntException \(Clase\)](../windows/safeintexception-class.md)