---
title: Constantes para el control de excepciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- EXCEPTION_CONTINUE_SEARCH
- c.constants
- EXCEPTION_CONTINUE_EXECUTION
- EXCEPTION_EXECUTE_HANDLER
dev_langs:
- C++
helpviewer_keywords:
- exception handling, constants
- EXCEPTION_CONTINUE_SEARCH constant
- EXCEPTION_EXECUTE_HANDLER constant
- EXCEPTION_CONTINUE_EXECUTION constant
- EH constants
ms.assetid: e1870f41-be9e-46a3-a2ea-830dfbaa18fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6cc17e429c0750b9f0cc8d9eb24bc94adf00484e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070605"
---
# <a name="exception-handling-constants"></a>Constantes para el control de excepciones

La constante `EXCEPTION_CONTINUE_SEARCH`, `EXCEPTION_CONTINUE_EXECUTION` o `EXCEPTION_EXECUTE_HANDLER` se devuelve cuando se produce una excepción durante la ejecución de la sección protegida de una instrucción **try-except**. El valor devuelto determina cómo se controla la excepción. Para más información, vea la [instrucción try-except](../cpp/try-except-statement.md) en la *Referencia del lenguaje C++*.

## <a name="see-also"></a>Vea también

[Constantes globales](../c-runtime-library/global-constants.md)