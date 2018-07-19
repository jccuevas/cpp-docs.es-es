---
title: Cuerpo de función | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6a566c1120f0a89a985895393fae5a79690bfa3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384683"
---
# <a name="function-body"></a>Cuerpo de función
Un "cuerpo de función" es una instrucción compuesta que contiene instrucciones que especifican lo que hace la función.  
  
## <a name="syntax"></a>Sintaxis  
 *function-definition*:  
 *declaration-specifiers* opt*attribute-seq* opt*declarator declaration-list* opt*compound-statement*  
  
 /\* *attribute-seq* es específico de Microsoft */  
  
 *compound-statement*: /\* cuerpo de la función \*/  
 **{**  *declaration-list* opt*statement-list* opt **}**  
  
 Las variables declaradas en el cuerpo de función, o "variables locales", tienen la clase de almacenamiento **auto** a menos que se especifique lo contrario. Cuando se llama a la función, se crea el almacenamiento para las variables locales y se realizan las inicializaciones locales. El control de ejecución pasa a la primera instrucción de *compound-statement* y continúa hasta que se ejecuta una instrucción `return` o hasta que se encuentra el final del cuerpo de función. A continuación, el control se devuelve al punto en el que se llamó a la función.  
  
 Una instrucción `return` que contiene una expresión debe ejecutarse si la función tiene que devolver un valor. El valor devuelto de una función es indefinido si no se ejecuta ninguna instrucción `return` o si la instrucción `return` no incluye una expresión.  
  
## <a name="see-also"></a>Vea también  
 [Definiciones de función de C](../c-language/c-function-definitions.md)