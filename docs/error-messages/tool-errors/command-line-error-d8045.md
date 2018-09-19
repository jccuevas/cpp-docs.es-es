---
title: Error de la línea de comandos D8045 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8045
dev_langs:
- C++
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6838202178e8012df61d17e2434461d6f4858bf3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022791"
---
# <a name="command-line-error-d8045"></a>Error de la línea de comandos D8045

no se puede compilar el archivo de C 'archivo' con la opción /clr

Sólo archivos de código de C++ fuente pueden pasarse a una compilación que usa **/CLR**.  Use **/TP** para compilar un archivo .c como un archivo .cpp; vea [/TC, / TP, / TC, /TP (Especificar tipo de archivo de origen)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) para obtener más información.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

También puede producirse D8045 si compila una aplicación ATL con Visual C++. Consulte [Cómo: migrar a/CLR](../../dotnet/how-to-migrate-to-clr.md) para obtener más información.