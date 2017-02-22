---
title: "Acceso a miembros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "acceso a miembros, operadores sobrecargados"
  - "operadores de selección de miembros"
  - "sobrecarga de operadores, operadores de acceso a miembros"
  - "punteros, inteligentes"
  - "punteros inteligentes"
  - "punteros inteligentes, definición"
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Acceso a miembros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El acceso a miembros de clase se puede controlar mediante la sobrecarga del operador de acceso a miembros \(**–\>**\).  Este operador se considera un operador unario en este uso, y la función de operador sobrecargado debe ser una función miembro de clase.  Por lo tanto, la declaración de una función de ese tipo es:  
  
## Sintaxis  
  
```  
  
class-type *operator–>()  
```  
  
## Comentarios  
 donde *class\-type* es el nombre de la clase a la que pertenece este operador.  La función de operador de acceso a miembros debe ser una función miembro no estática.  
  
 Este operador se usa \(a menudo junto con el operador de desreferenciación de puntero\) para implementar "punteros inteligentes" que validan punteros antes del uso de desreferenciación o de recuento.  
  
 El operador de acceso a miembros **.** no se puede sobrecargar.  
  
## Vea también  
 [Sobrecarga de operadores](../cpp/operator-overloading.md)