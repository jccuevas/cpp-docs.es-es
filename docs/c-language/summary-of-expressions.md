---
title: "Resumen de expresiones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resumen de expresiones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*primary\-expression*:  
 *identifier*  
  
 *constante*  
  
 *literal de cadena*  
  
 **\(**  *expression*  **\)**  
  
 *expression*:  
 *assignment\-expression*  
  
 *expression*  **,**  *assignment\-expression*  
  
 *constant\-expression*:  
 *conditional\-expression*  
  
 *conditional\-expression*:  
 *logical\-OR\-expression*  
  
 *logical\-OR\-expression*  **?**  *expression*  **:**  *conditional\-expression*  
  
 *assignment\-expression*:  
 *conditional\-expression*  
  
 *unary\-expression assignment\-operator assignment\-expression*  
  
 *postfix\-expression*:  
 *primary\-expression*  
  
 *postfix\-expression*  **\[**  *expression*  **\]**  
  
 *postfix\-expression*  **\(**  *argument\-expression\-list*  opt **\)**  
  
 *postfix\-expression*  **.**  *identifier*  
  
 *postfix\-expression*  **–\>**  *identifier*  
  
 *postfix\-expression*  **\+\+**  
  
 *postfix\-expression*  **––**  
  
 *argument\-expression\-list*:  
 *assignment\-expression*  
  
 *argument\-expression\-list*  **,**  *assignment\-expression*  
  
 *unary\-expression*:  
 *postfix\-expression*  
  
 **\+\+**  *unary\-expression*  
  
 **––**  *unary\-expression*  
  
 *unary\-operator*  
  
 *expresión\-conversión*  
  
 **sizeof**  *unary\-expression*  
  
 **sizeof \(**  *type\-name*  **\)**  
  
 *unary\-operator*: uno de  
 **& \* \+ – ~ \!**  
  
 *cast\-expression*:  
 *unary\-expression*  
  
 **\(**  *type\-name*  **\)**  *cast\-expression*  
  
 *expresión\-multiplicativa*:  
 *expresión\-conversión*  
  
 *multiplicative\-expression*  **\***  *cast\-expression*  
  
 *expresión\-multiplicativa*  **\/**  *expresión\-conversión*  
  
 *expresión\-multiplicativa*  **%**  *expresión\-conversión*  
  
 *additive\-expression*:  
 *multiplicative\-expression*  
  
 *additive\-expression*  **\+**  *multiplicative\-expression*  
  
 *additive\-expression*  **–**  *multiplicative\-expression*  
  
 *shift\-expression*:  
 *additive\-expression*  
  
 *shift\-expression*  **\<\<**  *additive\-expression*  
  
 *shift\-expression*  **\>\>**  *additive\-expression*  
  
 *relational\-expression*:  
 *shift\-expression*  
  
 *relational\-expression*  **\<**  *shift\-expression*  
  
 *relational\-expression*  **\>**  *shift\-expression relational\-expression*  **\<\=**  *shift\-expression*  
  
 *relational\-expression*  **\>\=**  *shift\-expression*  
  
 *equality\-expression*:  
 *relational\-expression*  
  
 *equality\-expression*  **\=\=**  *relational\-expression*  
  
 *equality\-expression*  **\!\=**  *relational\-expression*  
  
 *AND\-expression*:  
 *equality\-expression*  
  
 *AND\-expression*  **&**  *equality\-expression*  
  
 *exclusive\-OR\-expression*:  
 *AND\-expression*  
  
 *exclusive\-OR\-expression*  **^**  *AND\-expression*  
  
 *inclusive\-OR\-expression*:  
 *exclusive\-OR\-expression*  
  
 *inclusive\-OR\-expression*  **&#124;**   *exclusive\-OR\-expression*  
  
 *logical\-AND\-expression*:  
 *inclusive\-OR\-expression*  
  
 *logical\-AND\-expression*  **&&**  *inclusive\-OR\-expression*  
  
 *logical\-OR\-expression*:  
 *logical\-AND\-expression*  
  
 *logical\-OR\-expression*  **&#124;&#124;**  *logical\-AND\-expression*  
  
## Vea también  
 [Gramática de la estructura de la frase](../c-language/phrase-structure-grammar.md)