---
title: "CArrayRowset::operator | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CArrayRowset::operator[]"
  - "CArrayRowset.operator[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operador [], matrices"
  - "[] (operador)"
  - "operador[], matrices"
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CArrayRowset::operator
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona matriz\- como la sintaxis para tener acceso a una fila del conjunto de filas.  
  
## Sintaxis  
  
```  
  
      TAccessor  
      & operator[](int nRow);  
```  
  
#### Parámetros  
 `TAccessor`  
 Un parámetro con plantillas que especifica el tipo de descriptor de acceso almacenados en el conjunto de filas.  
  
 `nRow`  
 \[in\] Número de fila \(elemento de matriz\) que desea obtener acceso.  
  
## Valor devuelto  
 El contenido de la fila solicitada.  
  
## Comentarios  
 Si `nRow` supera el número de filas del conjunto de filas, se produce una excepción.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CArrayRowset \(Clase\)](../../data/oledb/carrayrowset-class.md)