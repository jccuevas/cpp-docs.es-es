---
title: Definiciones externas
ms.date: 11/04/2016
helpviewer_keywords:
- external definitions
- external linkage, variable declarations
ms.assetid: 41e37bfc-b360-43b1-9972-28af2d365b20
ms.openlocfilehash: 98694abd0598ce1e601a7da74c4681442a71f7df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597657"
---
# <a name="external-definitions"></a>Definiciones externas

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration*: /\* Solo permitida en el ámbito externo (archivo) \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*

*function-definition*: /\* El declarador aquí es el declarador de la función \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

## <a name="see-also"></a>Vea también

[Gramática de la estructura de la frase](../c-language/phrase-structure-grammar.md)