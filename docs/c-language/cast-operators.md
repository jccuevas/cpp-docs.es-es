---
title: "Operadores de conversi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operadores de conversión"
  - "operadores [C++], conversión"
  - "conversiones de tipos, operadores"
  - "conversión de tipos, operadores de conversión"
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Operadores de conversi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una conversión de tipo proporciona un método para la conversión explícita del tipo de un objeto en una situación concreta.  
  
## Sintaxis  
 *cast\-expression*:  
 *unary\-expression*  
  
 **\(**  *type\-name*  **\)**  *cast\-expression*  
  
 El compilador trata *cast\-expression* como tipo *type\-name* una vez realizada una conversión de tipo.  Las conversiones se pueden utilizar para convertir objetos de cualquier tipo escalar en cualquier otro tipo escalar.  Las conversiones de tipos explícitas están restringidas por las mismas reglas que determinan los efectos de las conversiones implícitas, que se describen en [Conversiones de asignación](../c-language/assignment-conversions.md).  Se pueden aplicar otras restricciones derivadas de los tamaños reales o de la representación de tipos específicos.  Vea [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md) para obtener información sobre los tamaños reales de los tipos enteros.  Para obtener más información sobre la conversión de tipos, vea [Conversiones de tipos](../c-language/type-cast-conversions.md).  
  
## Vea también  
 [Operador de conversión: \(\)](../cpp/cast-operator-parens.md)