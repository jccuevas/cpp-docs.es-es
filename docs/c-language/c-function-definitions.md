---
title: Definiciones de funciones de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a58adfefc5e2b3b5085a44c38dd392d3369421c8
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
---
# <a name="c-function-definitions"></a>Definiciones de funciones de C
Una definición de función especifica el nombre de la función, los tipos y el número de parámetros que espera recibir, y su tipo de valor devuelto. Una definición de función también incluye un cuerpo de la función con las declaraciones de las variables locales y las instrucciones que determinan lo que hace la función.  
  
## <a name="syntax"></a>Sintaxis  
 *translation-unit*:  
 *external-declaration*  
  
 *translation-unit external-declaration*  
  
 *external-declaration*: /\* Solo permitida en el ámbito externo (archivo) \*/  
 *function-definition*  
  
 `declaration`  
  
 *function-definition*: /\* El declarador aquí es el declarador de la función \*/  
 *declaration-specifiers* opt*attribute-seq* opt*declarator declaration-list* opt*compound-statement*  
  
 /\* *attribute-seq* es específico de Microsoft */  
  
 Los parámetros de prototipo son:  
  
 *declaration-specifiers*:  
 *storage-class-specifier declaration-specifiers* opt  
  
 *type-specifier declaration-specifiers* opt  
  
 *type-qualifier declaration-specifiers* opt  
  
 *declaration-list*:  
 *declaration*  
  
 *declaration-list declaration*  
  
 `declarator`:  
 *pointer* opt*direct-declarator*  
  
 *direct-declarator*: /\* Un declarador de función \*/  
 *direct-declarator*  **(**  *parameter-type-list*  **)** /* Declarador de estilo nuevo \*/  
  
 *direct-declarator*  **(**  *identifier-list* opt**)** /* Declarador de estilo obsoleto \*/  
  
 La lista de parámetros de una definición utiliza esta sintaxis:  
  
 *parameter-type-list*: /\* La lista de parámetros \*/  
 *parameter-list*  
  
 *parameter-list* **, ...**  
  
 *parameter-list*:  
 *parameter-declaration*  
  
 *parameter-list* **,**  *parameter-declaration*  
  
 *parameter-declaration*:  
 *declaration-specifiers declarator*  
  
 *declaration-specifiers abstract declarator* opt  
  
 La lista de parámetros de una definición de función de estilo antiguo utiliza esta sintaxis:  
  
 *identifier-list*: /\* utilizado en definiciones de función y declaraciones de estilo obsoleto \*/  
 *identifier*  
  
 *identifier-list* **,**  *identifier*  
  
 La sintaxis para el cuerpo de la función es:  
  
 *compound-statement*: /\* cuerpo de la función \*/  
 **{**  `declaration`-*list* opt*statement-list* opt**}**  
  
 Los únicos especificadores de clase de almacenamiento que pueden modificar una declaración de función son `extern` y **static**. El especificador `extern` significa que se puede hacer referencia a la función desde otros archivos; es decir, el nombre de función se exporta al vinculador. El especificador **static** significa que no se puede hacer referencia a la función desde otros archivos; es decir, el vinculador no exporta el nombre. Si no aparece ninguna clase de almacenamiento en una definición de función, se supone `extern`. En cualquier caso, la función siempre es visible desde el punto de definición hasta el final del archivo.  
  
 Los especificadores *declaration-specifiers`declarator` opcionales y el parámetro*  obligatorio juntos especifican el tipo de valor devuelto y el nombre de la función. `declarator` es una combinación del identificador que proporciona el nombre de la función y los paréntesis que siguen al nombre de la función. El parámetro *attribute-seq* opcional no terminal es una característica específica de Microsoft que se define en [Atributos de función](../c-language/function-attributes.md).  
  
 El *direct-declarator* (en la sintaxis de `declarator`) especifica el nombre de la función que se define y los identificadores de sus parámetros. Si el *direct-declarator* incluye una *parameter-type-list*, la lista especifica los tipos de todos los parámetros. Un declarador de este tipo también actúa como un prototipo de función para las llamadas posteriores a la función.  
  
 Un parámetro `declaration` de la *declaration-list* en las definiciones de función no puede contener un *storage-class-specifier* distinto de **register**. El elemento *type-specifier* en la sintaxis de los especificadores *declaration-specifiers* se puede omitir solo si se especifica la clase de almacenamiento **register** para un valor de tipo `int`.  
  
 El elemento *compound-statement* es el cuerpo de la función que contiene las declaraciones de variables locales, las referencias a elementos declarados externamente y las instrucciones.  
  
 En las secciones [Atributos de función](../c-language/function-attributes.md), [Clase de almacenamiento](../c-language/storage-class.md), [Tipo de valor devuelto](../c-language/return-type.md), [Parámetros](../c-language/parameters.md) y [Cuerpo de la función](../c-language/function-body.md) se describen los componentes de la definición de función en detalle.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../c-language/functions-c.md)