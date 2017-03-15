---
title: Resumen de declaraciones | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: cf1442e98cdd7489a395bec211cda1bbb037bae2
ms.lasthandoff: 02/24/2017

---
# <a name="summary-of-declarations"></a>Resumen de declaraciones
`declaration`:  
 *declaration-specifiers attribute-seq* opt*init-declarator-list*opt**;**  
  
 /\* *attribute-seq* es específico de Microsoft */  
  
 *declaration-specifiers*:  
 *storage-class-specifier declaration-specifiers*opt  
  
 *type-specifier declaration-specifiers*opt  
  
 *type-qualifier declaration-specifiers*opt  
  
 *attribute-seq* :            /\* *attribute-seq* es específico de Microsoft \*/  
 *attribute attribute-seq* opt  
  
 *attribute* : one of      /* Específico de Microsoft\*/  
 ||||  
|-|-|-|  
|[__asm](../assembler/inline/asm.md)|[__clrcall](../cpp/clrcall.md)|[__stdcall](../cpp/stdcall.md)|  
|[__based](../cpp/based-grammar.md)|[__fastcall](../cpp/fastcall.md)|[__thiscall](../cpp/thiscall.md)|  
|[__cdecl](../cpp/cdecl.md)|[__inline](../cpp/inline-functions-cpp.md)|[__vectorcall](../cpp/vectorcall.md)|  
  
 *init-declarator-list*:  
 *init-declarator*  
  
 *init-declarator-list*  **,**  *init-declarator*  
  
 *init-declarator*:  
 *declarator*  
  
 *declarator*  **=**  *initializer* /* Para la inicialización de valores escalares \*/  
  
 *storage-class-specifier*:  
 **auto**  
  
 **register**  
  
 **static**  
  
 **extern**  
  
 **typedef**  
  
 **__declspec (**  *extended-decl-modifier-seq*  **)** /* Específico de Microsoft \*/  
  
 *type-specifier*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 `__int8` /* Específico de Microsoft\*/  
  
 `__int16` /* Específico de Microsoft\*/  
  
 `__int32` /* Específico de Microsoft\*/  
  
 `__int64` /* Específico de Microsoft\*/  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct-or-union-specifier*  
  
 *enum-specifier*  
  
 *typedef-name*  
  
 *type-qualifier*:  
 **const**  
  
 `volatile`  
  
 `declarator`:  
 `pointer`opt*direct-declarator*  
  
 *direct-declarator*:  
 *identifier*  
  
 **(**  *declarator*  **)**  
  
 *direct-declarator*  **[**  *constant-expression* opt**]**  
  
 *direct-declarator*  **(**  *parameter-type-list*  **)** /* Declarador de estilo nuevo \*/  
  
 *direct-declarator*  **(**  *identifier-list*opt**)** /* Declarador de estilo obsoleto \*/  
  
 `pointer`:  
 **\*** *type-qualifier-list*opt  
  
 **\*** *type-qualifier-list*opt`pointer`  
  
 *parameter-type-list*:                           /\* La lista de parámetros \*/  
 *parameter-list*  
  
 *parameter-list* **, ...**  
  
 *parameter-list*:  
 *parameter-declaration*  
  
 *parameter-list*  **,**  *parameter-declaration*  
  
 *type-qualifier-list*:  
 *type-qualifier*  
  
 *type-qualifier-list type-qualifier*  
  
 *enum-specifier*:  
 **enum**  *identifier*opt**{** *enumerator-list* **}**  
  
 **enum**  *identifier*  
  
 *enumerator-list*:  
 *enumerator*  
  
 *enumerator-list*  **,**  `enumerator`  
  
 `enumerator`:  
 *enumeration-constant*  
  
 *enumeration-constant*  **=**  *constant-expression*  
  
 *enumeration-constant*:  
 *identifier*  
  
 *struct-or-union-specifier*:  
 *struct-or-union identifier*opt**{** *struct-declaration-list* **}** *struct-or-union identifier*  
  
 *struct-or-union*:  
 **struct**  
  
 **union**  
  
 *struct-declaration-list*:  
 *struct-declaration*  
  
 *struct-declaration-list struct-declaration*  
  
 *struct-declaration*:  
 *specifier-qualifier-list struct-declarator-list* **;**  
  
 *specifier-qualifier-list*:  
 *type-specifier specifier-qualifier-list*opt  
  
 *type-qualifier specifier-qualifier-list*opt  
  
 *struct-declarator-list*:  
 *struct-declarator struct-declarator-list*  **,**  *struct-declarator*  
  
 *struct-declarator*:  
 *declarator*  
  
 *type-specifier declarator*opt**:** *constant-expression*  
  
 *parameter-declaration*:  
 *declaration-specifiers declarator* /* Declarador con nombre\*/  
  
 *declaration-specifiers abstract-declarator*opt**/\*** Declarador anónimo **\*/**  
  
 *identifier-list*: **/\*** Para el declarador de estilo antiguo **\* /**  
 *identifier*  
  
 *identifier-list*  **,**  *identifier*  
  
 *abstract-declarator*: **/\*** Usado con declaradores anónimos **\*/**  
 *pointer*  
  
 `pointer`opt*direct-abstract-declarator*  
  
 *direct-abstract-declarator*:  
 **(**  *abstract-declarator*  **)**  
  
 *direct-abstract-declarator*opt**[** *constant-expression*opt**]**  
  
 *direct-abstract-declarator*opt**(** *parameter-type-list* opt**)**  
  
 *initializer*:  
 *assignment-expression*  
  
 **{**  *initializer-list*  **}** /* Para la inicialización de agregados \*/  
  
 **{**  *initializer-list*  **, }**  
  
 *initializer-list*:  
 *initializer*  
  
 *initializer-list*  **,**  *initializer*  
  
 *type-name*:  
 *specifier-qualifier-list abstract-declarator*opt  
  
 *typedef-name*:  
 *identifier*  
  
 *extended-decl-modifier-seq*:/\*    Específico de Microsoft \*/  
 *extended-decl-modifier*opt  
  
 *extended-decl-modifier-seq extended-decl-modifier*  
  
 *extended-decl-modifier*:   /\* Específico de Microsoft \*/  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)   
 [Gramática de la estructura de la frase](../c-language/phrase-structure-grammar.md)   
 [Convenciones de llamada obsoletas](../cpp/obsolete-calling-conventions.md)
