---
title: Resumen de tokens
ms.date: 11/04/2016
ms.assetid: 2978cbf6-e66e-46fc-9938-caa052f2ccf7
ms.openlocfilehash: f295f59ce5767fce5416dde3545188cb0b1d4408
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549544"
---
# <a name="summary-of-tokens"></a>Resumen de tokens

*token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*keyword*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*preprocessing-token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*header-name*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*character-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator punctuator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;cada carácter de espacio que no sea en blanco que no pueda ser uno de los anteriores

*header-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\<**  *path-spec*  **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"**  *path spec*  **"**

*path-spec*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Ruta de acceso válida

*pp-number*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**.** *digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *digit* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **e**  *sign*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **E**  *sign*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **.**

## <a name="see-also"></a>Vea también

[Gramática léxica](../c-language/lexical-grammar.md)