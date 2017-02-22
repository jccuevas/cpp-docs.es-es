---
title: "Gram&#225;tica del preprocesador | Microsoft Docs"
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
  - "gramática, preprocesador"
  - "preprocesador"
  - "preprocesador, gramática"
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Gram&#225;tica del preprocesador
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\#define**  *identifier* *token\-string*opt  
  
 *\#* **define**  *identifier*\[**\(** *identifier*opt**,** *...* **,** *identifier*opt **\)**\] *token\-string*opt  
  
 **defined\(**  *identifier* **\)**  
  
 **defined**  *identifier*  
  
 `#include` **"***path\-spec***"**  
  
 `#include` **\<***path\-spec***\>**  
  
 **\#line**  *digit\-sequence*  **"** *filename* **"** opt  
  
 *\#* **undef**  *identifier*  
  
 **\#error**  *token\-string*  
  
 **\#pragma**  *token\-string*  
  
 *conditional* :  
 *if\-part elif\-parts* opt *else\-part*opt *endif\-line*  
  
 *if\-part* :  
 *if\-linetext*  
  
 *if\-line* :  
 **\#if**  *constant\-expression*  
  
 **\#ifdef**  *identifier*  
  
 **\#ifndef**  *identifier*  
  
 *elif\-parts* :  
 *elif\-line text*  
  
 *elif\-parts elif\-line text*  
  
 *elif\-line* :  
 **\#elif**  *constant\-expression*  
  
 *else\-part* :  
 *else\-linetext*  
  
 *else\-line* :  
 `#else`  
  
 *endif\-line* :  
 `#endif`  
  
 *digit\-sequence* :  
 *digit*  
  
 *digit\-sequence digit*  
  
 *digit* : uno de  
 **0 1 2 3 4 5 6 7 8 9**  
  
 *token\-string* :  
 cadena de tokens  
  
 *token* :  
 *palabra clave*  
  
 *identifier*  
  
 *constante*  
  
 *operador*  
  
 `punctuator`  
  
 *filename* :  
 nombre de archivo del sistema operativo válido  
  
 *path\-spec* :  
 Ruta de acceso válida  
  
 *text* :  
 cualquier secuencia de texto  
  
> [!NOTE]
>  Los elementos no terminales siguientes se describen con más detalle en el Apéndice A, [Resumen de la gramática](../misc/grammar-summary-cpp.md), de la *Referencia del lenguaje C\+\+*: `constant`, `constant`\-*expression*, *identifier*, *keyword*, `operator` y `punctuator`.  
  
## Vea también  
 [Resumen de la gramática](../preprocessor/grammar-summary-c-cpp.md)