---
title: "_com_ptr_t (Extractores) | Microsoft Docs"
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
  - "_com_ptr_t::operatorInterface&"
  - "operatorInterface*"
  - "operatorInterface&"
  - "_com_ptr_t::operatorbool"
  - "_com_ptr_t.operator->"
  - "_com_ptr_t.operator*"
  - "_com_ptr_t::operator->"
  - "_com_ptr_t::operator*"
  - "_com_ptr_t.operatorInterface&"
  - "_com_ptr_t.operatorbool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& (operador), con objetos específicos"
  - "* (operador), con objetos específicos"
  - "-> (operador), con objetos específicos"
  - "extractores"
  - "extractores, _com_ptr_t (clase)"
  - "operador *"
  - "operador bool"
  - "operador Interface&"
  - "operador Interface*"
  - "operator&"
  - "operator*"
  - "operator->"
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t (Extractores)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Extrae el puntero de interfaz COM encapsulado.  
  
## Sintaxis  
  
```  
  
      operator Interface*( ) const throw( );   
operator Interface&( ) const;   
Interface& operator*( ) const;   
Interface* operator->( ) const;   
Interface** operator&( ) throw( );   
operator bool( ) const throw( );  
```  
  
## Comentarios  
  
-   **operator Interface\*** Devuelve el puntero de interfaz encapsulado, que puede ser **NULL**.  
  
-   **operator Interface&** Devuelve una referencia al puntero de interfaz encapsulado y emite un error si el puntero es **NULL**.  
  
-   **operator\*** Permite que un objeto de puntero inteligente actúe como si fuera la interfaz encapsulada real cuando se desreferencia.  
  
-   **operator\-\>** Permite que un objeto de puntero inteligente actúe como si fuera la interfaz encapsulada real cuando se desreferencia.  
  
-   **operator&** Libera cualquier puntero de interfaz encapsulado, lo reemplaza con **NULL** y devuelve la dirección del puntero encapsulado.  Esto permite pasar el puntero inteligente por dirección a una función que tenga un parámetro **out** a través del cual devuelve un puntero de interfaz.  
  
-   **operator bool** Permite usar un objeto de puntero inteligente en una expresión condicional.  Este operador devuelve **true** si el puntero no es **NULL**.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_ptr\_t \(Clase\)](../cpp/com-ptr-t-class.md)