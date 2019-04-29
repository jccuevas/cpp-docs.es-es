---
title: Error de la línea de comandos D8045
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 7964c2539b5358d2d946e530c4ee75110857446d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214201"
---
# <a name="command-line-error-d8045"></a>Error de la línea de comandos D8045

no se puede compilar el archivo de C 'archivo' con la opción /clr

Sólo archivos de código de C++ fuente pueden pasarse a una compilación que usa **/CLR**.  Use **/TP** para compilar un archivo .c como un archivo .cpp; vea [/TC, / TP, / TC, /TP (Especificar tipo de archivo de origen)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) para obtener más información.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

También puede producirse D8045 si compila una aplicación ATL con Visual C++. Vea [Cómo: Migrar a/CLR](../../dotnet/how-to-migrate-to-clr.md) para obtener más información.