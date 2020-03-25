---
title: Resumen de declaraciones
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: e553f4bdfffcd4bba6a39b2d37af6ba25a3d65d9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170441"
---
# <a name="summary-of-declarations"></a>Resumen de declaraciones

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-Specifier* *Attribute-SEQ*<sub>OPT</sub> *init-declarator-List*<sub>OPT</sub> **;**

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-Class-Specifier* *declaration-Specifier*<sub>OPC</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;declaración *-especificador de tipo* *-especificadores*<sub>OPC</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;declaración de *calificador de tipo* *: especificadores*<sub>OPT</sub>

*Attribute-SEQ* :&nbsp;&nbsp;&nbsp;&nbsp;/\* \*específico de Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;atributo *Attribute* *-Seq*<sub>OPC</sub>

*Attribute* : uno de&nbsp;&nbsp;&nbsp;&nbsp;/\* \*específico de Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall __thiscall](../cpp/fastcall.md) [__cdecl __inline](../cpp/thiscall.md) [__vectorcall](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-List* **,** *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarador* **=** *inicializador* /\* para la inicialización escalar \*/

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**auto**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**register**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *Extended-decl-Modifier-SEQ* **)**  /\* \*específico de Microsoft /

*type-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int8** /\* \*específico de Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int16** /\* \*específico de Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int32** /\* \*específico de Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int64** /\* \*específico de Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**signed**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**unsigned**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*type-qualifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**const**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**volatile**

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*puntero*<sub>OPT</sub> *Direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *declarador* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-declarator* **[** *Constant-Expression*<sub>OPC</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-declarator* **(** *Parameter-Type-List* **)**  /\* declarador de estilo nuevo \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-declarator* **(** *Identifier-List*<sub>OPT</sub> **)**  /\* declarador de estilo obsoleto \*/

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Type-Qualifier-List*<sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> <sub>opt</sub> *puntero* de *tipo de calificador de lista*

*parameter-type-list*:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* La lista de parámetros \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,...**

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*lista de parámetros* **,** *declaración de parámetros*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Type *-Qualifier-List* *-Qualifier*

*enum-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificador*de **enumeración** <sub>OPC</sub> **{** *enumerador-lista* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificador* de **enumeración**

*enumerator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerador-lista* **,** *enumerador*

*enumerator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeración-constante* **=** *constante-expresión*

*enumeration-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;identificador *struct-or-Union* *identifier*<sub>OPC</sub> **{** *struct-declaration-List* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificador* *struct-or-Union*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**struct**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**union**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration-List* *-declaration*

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*especificador-Qualifier-List* *struct-declarator-List* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;especificador de *tipo-especificador* *-calificador-lista*<sub>OPC</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;especificador de *calificador de tipo* *(Qualifier-List)* <sub>OPC</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declarador* *struct-declarator-List* **,** *struct-declarator*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarador* *de tipo-especificador* <sub>OPT</sub> **:** *Constant-Expression*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-Specifier* *declarator* /\* declarador con nombre \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-Specifiers* *abstract-declarator*<sub>OPT</sub> /\* declarador anónimo \*/

*identifier-list*: /\* Para el declarador de estilo antiguo \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificador-lista* **,** *identificador*

*abstract-declarator*: /\* Usado con declaradores anónimos \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*puntero*<sub>OPT</sub> *Direct-Abstract-declarator*

*direct-abstract-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *abstract-declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-Abstract-declarator*<sub>OPT</sub> **[** *Constant-Expression*<sub>OPC</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-Abstract-declarator*<sub>OPT</sub> **(** *Parameter-Type-List*<sub>OPT</sub> **)**

*initializer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *initializer-List* **}**  /\* para la inicialización agregada \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *initializer-List* **,}**

*initializer-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inicializador-lista* **,** *inicializador*

*type-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*especificador-Qualifier-List* *abstract-declarator*<sub>OPT</sub>

*typedef-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*Extended-decl-Modifier-SEQ*:&nbsp;&nbsp;&nbsp;&nbsp;/\* \*específico de Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-Modifier-SEQ* *Extended-decl-Modifier*

*Extended-decl-Modifier*:&nbsp;&nbsp;&nbsp;&nbsp;/\* \*específico de Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Consulte también

[Convenciones de llamada](../cpp/calling-conventions.md)<br/>
[Gramática de la estructura de la frase](../c-language/phrase-structure-grammar.md)<br/>
[Convenciones de llamada obsoletas](../cpp/obsolete-calling-conventions.md)
