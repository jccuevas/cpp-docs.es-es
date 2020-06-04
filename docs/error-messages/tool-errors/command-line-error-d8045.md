---
title: Error de la línea de comandos D8045
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 05a2d3851e58062e1e326781a223e2f4b0346620
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196851"
---
# <a name="command-line-error-d8045"></a>Error de la línea de comandos D8045

no se puede compilar el archivo de C ' file ' con la opción/CLR

Solo C++ los archivos de código fuente se pueden pasar a una compilación que utiliza **/CLR**.  Use **/TP** para compilar un archivo. c como archivo. cpp; vea [/TC,/TP,/TC,/TP (especificar el tipo de archivo de origen)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) para obtener más información.

Para obtener más información, consulta [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 también se puede producir si se compila una aplicación ATL mediante C++visual. Consulte [Cómo: migrar a/CLR](../../dotnet/how-to-migrate-to-clr.md) para obtener más información.
