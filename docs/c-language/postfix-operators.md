---
title: Operadores de postfijo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ad53a3993bfc55b51cab05d5eca1a10d44bd2c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="postfix-operators"></a>Operadores de postfijo
Los operadores de postfijo tienen la máxima prioridad (el enlace más estricto) en la evaluación de una expresión.  
  
## <a name="syntax"></a>Sintaxis  
 *postfix-expression*:  
 *primary-expression*  
  
 *postfix-expression*  **[**  *expression*  **]**  
  
 *postfix-expression*  **(**  *argument-expression-list* opt**)**  
  
 *postfix-expression*  **.**  *identifier*  
  
 *postfix-expression*  **->**  *identifier*  
  
 *postfix-expression*  **++**  
  
 *postfix-expression*  **--**  
  
 Los operadores en este nivel de prioridad son los subíndices de matriz, las llamadas a función, los miembros de estructura y unión, y los operadores postfijos de incremento y decremento.  
  
## <a name="see-also"></a>Vea también  
 [Operadores de C](../c-language/c-operators.md)